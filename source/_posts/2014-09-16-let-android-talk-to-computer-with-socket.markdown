---
layout: post
title: "Let Android Talk to Computer with Socket"
date: 2014-09-16 21:45:17 +0800
comments: true
categories: Android
---

在没有公网/wifi的情况下让 Android 手机通过 USB 或者让虚拟机里的 Android 系统与电脑进行通信。

<!-- more -->

基本原理是当 Android 手机通过 USB 连接电脑时，两者之间就形成了一个局域网（具体是由 ADB 实现的）。
嗯，看到这里只要了解网络编程的同学就知道怎么做了。
就是把 Android 手机作为服务器，监听某个端口来获取客户端连接,而 PC 可以作为客户端。
这里的问题是客户端要怎么连接到服务器的端口，这个需要运行 adb shell 指令 ：
    
	adb.exe forward tcp:[port1] tcp:[port2]  // port1: PC 上的端口; port2: Android 上的端口。此处会把 PC 上发往 port1 的信息转发至 Android 的 port2
	
Android 服务器代码：

	void startServer() {
		ServerSocket serverSocket = null;
		
		try {
			Log.e("Android", "start to accpet");
			
			serverSocket = new ServerSocket(SERVER_PORT); // 即 port2
		
			while (true) {
				Socket client = serverSocket.accept();
			
				Log.e("Android", "receive client");
				
				try {
					BufferedReader in = new BufferedReader(new InputStreamReader(client.getInputStream()));
					final String str = in.readLine();
				
					Log.e("Android", str);
					
					runOnUiThread(new Runnable() {
						@Override
						public void run() {
							show.setText(str);
						}
					});
					
					PrintWriter out = new PrintWriter(new BufferedWriter(new OutputStreamWriter(client.getOutputStream())),true);
					out.println("I'm Android");
					in.close();
					out.close();
				} catch (Exception e) {
					Log.e("Android", "");
					e.printStackTrace();
				} finally {
					client.close();
					Log.e("Android", "");
				}
				Thread.sleep(3000);
			}
		} catch (Exception e) {
			Log.e("Android", "");
			e.printStackTrace();
		} finally {
			if (serverSocket != null) {
				try {
					serverSocket.close();
				} catch (IOException e) {
					e.printStackTrace();
				}
			}
		}
	}
	
PC 客户端代码：

	try {
			// 6665是 PC 端的端口，通过运行该 Shell 命令重定向到 Android Device 的6666端口 (端口自己定，不得超过1023)
			Runtime.getRuntime().exec("[Your Android SDK's Dir]\\platform-tools\\adb.exe forward tcp:6665 tcp:6666");
		} catch (IOException e) {
			e.printStackTrace();
			return;
		}

		Socket socket = null;
		try {
			InetAddress serverAddr = null;
			serverAddr = InetAddress.getByName("127.0.0.1");
			System.out.println("Start to connect android");

			socket = new Socket(serverAddr, 6665);

			String message = "I'm pc";
			System.out.println("Pc is sending message: " + message);
			PrintWriter out = new PrintWriter(new BufferedWriter(new OutputStreamWriter(socket.getOutputStream())), true);
			out.println(message);
			Thread.sleep(5000);
			
			// receive message from server (Android Device)
			BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
			String msg = br.readLine();
			System.out.println(msg);
		} catch (UnknownHostException e) {
			System.out.println(e);
		} catch (IOException e) {
			System.out.println(e);
		} finally {
			try {
				if (socket != null) {
					socket.close();
				}
			} catch (IOException e) {
				System.out.println(e);
			}
		}
	}
