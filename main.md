# 面试考题整理


## 1，编写一个算法，若M*N矩阵中某个元素为0，则将其所在的行与列清零。

    private static void filter(int[][] args) {
        boolean[] row = new boolean[args.length];
        boolean[] column = new boolean[args[0].length];
        for (int i = 0; i < args.length; i++) {
            for (int j = 0; j < args[0].length; j++) {
                if (args[i][j] == 0) {
                    row[i] = true;
                    column[j] = true;
                }
            }
        }
        for (int i = 0; i < args.length; i++) {
            for (int j = 0; j < args[0].length; j++) {
                if (row[i] || column[j]) {
                    args[i][j] = 0;
                }
            }
        }
    }



## 2，用java写一个会导致死锁的程序


    	final Object lock1 = new Object();
        final Object lock2 = new Object();
        Thread thread1 = new Thread() {
            @Override
            public void run() {
                super.run();
                System.out.printf("Thread1 lock1 before\n");
                synchronized (lock1) {
                    System.out.printf("Thread1 lock1 after\n");
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.printf("Thread1 lock2 before\n");
                    synchronized (lock2) {
                        System.out.printf("Thread1 lock2 after\n");
                    }
                }
            }
        };
        Thread thread2 = new Thread() {
            @Override
            public void run() {
                super.run();
                System.out.printf("Thread2 lock2 before\n");
                synchronized (lock2) {
                    System.out.printf("Thread2 lock2 after\n");
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.printf("Thread2 lock1 before\n");
                    synchronized (lock1) {
                        System.out.printf("Thread2 lock1 after\n");
                    }
                }
            }
        };

        thread1.start();
        thread2.start();