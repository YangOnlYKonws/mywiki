## Java贩卖机

为什么我要写一个贩卖机呢，第一目的是理解Java与C的不同区别，虽然我写的这个没有用很多的类定义，也没用到接口，但是我的想法是，这何尝不是一种对话的尝试，我在上课的时候学到这个地方，老师当时举的是贩卖机的例子，我首先想到的是RPG游戏的商人，然后是商人的折扣功能，然后是对话，因为这个可拓展功能可以实现多种方面串联起来，引起多种方面的结果。

最早开始的时候，我是想用多种**类**，多种**接口**，然后用上继承的方法来写这么一个东西，从而巩固我刚学的Java知识，现在这个**Part I**版本只能巩固基础语法，后续会推出**Part II**来实现我所说的多类，多借口，继承。

```java
import java.util.Random;
import java.util.Scanner;

public class potOfGreed {
    public static final double[] prince = {15.5,20.4,20.9};
    public static final String[] goodsName = {"治疗药水","魔力药水","传送卷轴"};
    public static final int goodsKind = prince.length;
    public static final double discountMax = 1.0;
    public static final double discountMin = 0.0;
    public static final Random random = new Random(); //1.基础点

    public static void main(String[] args) {
        double discount = randomDiscount(); //2.基础点
        System.out.printf("强欲之壶！小子！今日折扣是%.1f\n", discount);

        Scanner scanner = new Scanner(System.in); //3.基础点
        while(true) {
            System.out.println("你想要我给你变啥出来：");
            for(int i = 0;i < goodsKind;i++) {
                double princeDis = prince[i] * (1-discount);
                System.out.printf("序号：%d,名称：%s,价格：%.1f\n", i+1, 
                goodsName[i], princeDis); //4.基础点
            }
            System.out.println("0. 退出");

            int choice = scanner.nextInt();
            if(choice == 0) {
                break;
            }
            else if(choice < 1 || choice > 3) {
                System.out.println("你当强欲之壶是傻逼吗，选个没有的");
                continue;
            }

            System.out.printf("快点给我%.1f币！强欲之壶不可能凭空变出来！\n",
            prince[choice-1] * (1-discount));
            double coins = scanner.nextDouble();
            if(coins < prince[choice-1] * (1-discount) && coins != 
            prince[choice-1] * (1-discount)) { 
                System.out.println("你是想空手套白狼吗，给我稍微认真点阿！");
                continue;
            }

            double charge = coins - prince[choice-1] * (1-discount);
            System.out.printf("找你%.1f\n",charge);
        }
    }
    private static double randomDiscount() { //5.基础点
        return discountMin + (discountMax - discountMin) * 
        random.nextDouble();
    }
}
```

1. 基础点：随机赋值的运用
2. 基础点：构造函数的运用
3. 基础点：输入的运用
4. 基础点：类似C语言输出的方式
5. 基础点：构造函数