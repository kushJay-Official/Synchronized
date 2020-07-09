package synchrzd;

public class InterThreadComm {
    public static void main(String[] args) {
         Que q1=new Que();
         Producer p1= new Producer(q1);
         p1.start();
         Consmr c1=new Consmr(q1);
         c1.start();
    }
}

public class Consmr extends Thread {
    private Que cq;
    public Consmr(Que q){
        cq=q;
    }
    public void run(){
        while(true)
            cq.get();
    }
}

public class Producer extends Thread{
    private Que pq;
    public Producer(Que q){
        pq=q;
    }
    public void run(){
        while (true){
            int i=0;
            pq.put(i++);
        }
    }
}

public class Que {
    private int num;
    private boolean flg;
    public Que() {
        flg = false;
    }
    synchronized void put(int n){
        while (flg==true) {
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
            num= n;
            System.out.println("Put In Q:"+num);
            flg=true;
            notify();
    }
    synchronized void get(){
        while (flg == false){
            try {
                wait();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        System.out.println("Got from Q:"+num);
        flg=false;
        notify();
    }
}
