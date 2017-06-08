## 单词翻转

    public static String reverseWords(String source) {
        String[] words = new String[source.length()];
        for (int i = 0; i < source.length(); i++) {
            words[i] = String.valueOf(source.charAt(i));
        }
        Collections.reverse(Arrays.asList(words));
        return join(words, "");
    }

    public static <T> String join(T[] arrys, CharSequence delimiter) {
        if (arrys == null) {
            return "";
        }
        StringBuilder sb = new StringBuilder();
        for (T o : arrys) {
            if (sb.length() > 0) {
                sb.append(delimiter);
            }
            sb.append(o);
        }
        return sb.toString();
    }