## 1到n，求1的个数


    //1-N  获取1的次数
    public static int getOneCount(int num) {
        int count = 0;
        for (int i = 0; i <= num; i++) {
            count += getCount(i);
        }
        return count;
    }

    public static int getCount(int num) {
        int count = 0;
        while (num > 0) {
            if (num % 10 == 1) {
                count++;
            }
            num = num / 10;
        }
        return count;
    }