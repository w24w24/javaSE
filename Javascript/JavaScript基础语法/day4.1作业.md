# 学完循环之后的作业

1.使用for循环打印9*9乘法表

2.接收用户输入的“用户名”、“密码”，用户名为“admin”、“12345”，如果用户输入的是，则提示用户输入成功，不是则弹出一直让用户输入

3.求整数1——100的累加和，但是要求跳过所有个位数为3的数【使用continue实现】

## 小组项目：

简易ATM取款机：

1.里面存有100块钱

2.如果存钱，就使用输入的钱加上先前的100，之后弹出显示余额提示框

3.如果取钱，就减去取的钱，之后弹出余额提示框

4.如果显示余额，就直接弹出余额

5.如果退出，弹出退出提示框

```javaScript
<script>
    var money = 100;// 这是原本的金额
    // 只有输入4的时候才可以退出 且保证输入123不退出循环
    while (true) {
        var choice = Number(prompt('请输入您要的操作：' + '\n' + '1、存钱' + '\n'
            + '2、取钱' + '\n' + '3、显示余额' + '\n' + '4、退出'));
        // 第一步:在银行里面存钱
        if (choice === 1) {
            var money1 = prompt('请输入您要存入的金额：');
            money += parseFloat(money1);
            alert('当前余额为：' + money);
        }
        /* 第二步：从银行卡里取钱
           但是要注意的是，取出的金额不可以大于银行里的余额
         */
        else if (choice === 2) {
            var money2 = prompt('请输入您要取出的金额：');
            if (money2 <= money) {
                money -= parseFloat(money2);
                alert('余额是：' + money);
            } else {
                alert('余额不足');
            }
        }
            // 第三步：查看银行卡余额
            else if (choice === 3) {
                alert('当前余额为：' + money);
            }
            //退出
        else if (choice === 4) {
            alert('正在退出...');
            break;
        }else {
            // 必须确保用户输入的指令是正确的
            alert('请输入正确的指令');
        }
    }
</script>
```