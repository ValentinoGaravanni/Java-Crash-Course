package OOP;

import java.util.HashMap;
import java.util.Map;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

abstract class Encoder {
    public abstract String encode(String source);
}

public class Leetspeak extends Encoder {
    private static final Map<String, String> coding = new HashMap<String, String>() {{
        put("a", "4");
        put("e", "3");
        put("l", "1");
        put("m", "/^^\\");
        put("o", "0");
        put("u", "(_)");
    }};

    public String encode(String source) {
        if (source == null)
            return "";
        String res = source;
        StringBuffer sb = new StringBuffer();
        for (String ch : coding.keySet()) {
            res = res.replaceAll("(?i)" + ch, Matcher.quoteReplacement(coding.get(ch)));
        }
        return res;
    }

    public static void main(String[] args) {
        System.out.println(new Leetspeak().encode("l83Gq3aAq I UjW9e1szmn YN 7b0"));
    }
}