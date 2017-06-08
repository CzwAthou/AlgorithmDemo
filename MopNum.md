## 猫扑素数：
以2 开头, 之后跟任意多个 3 的十进制整数而且是个素数, 则它是猫扑素数. 如 2, 23, 233, 2333, 23333 都是猫扑素数, 而 233333 则不是, 它可以分解为 353 x 661.


    
	/**
     * 是否为猫扑数
     *
     * @param num
     * @return
     */
    public static boolean isMopNum(int num) {
        if (num < 10) {
            return num == 2;
        } else {
            return (num % 10 == 3) && isMopNum(num / 10);
        }
    }

    /**
     * 是否为素数
     *
     * @return
     */
    public static boolean isPrimeNum(int num) {
        if (num < 2) { //素数从2开始，小于2的话不是素数
            return false;
        }
        for (int i = 2; i <= Math.sqrt(num); i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }