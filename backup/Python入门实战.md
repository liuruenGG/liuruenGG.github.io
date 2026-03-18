# Python 入门实战：写一个属于自己的实用小程序

## 为什么选择 Python？
在众多编程语言中，Python 绝对是对新手最友好的语言之一。它语法简洁、接近自然语言，而且拥有极其庞大的第三方库生态。无论是数据分析、人工智能，还是写个简单的自动化脚本，Python 都能轻松搞定。

## 实战演练：写一个专属的“番茄工作法”倒计时器
今天我们不讲枯燥的理论，直接动手写一个实用的小工具——命令行版番茄钟。
下面是源码分享：

```python
import time

def pomodoro_timer(minutes):
    seconds = minutes * 60
    print(f"🍅 专注时间开始！目标：{minutes} 分钟")
    
    while seconds > 0:
        mins, secs = divmod(seconds, 60)
        timer = f'{mins:02d}:{secs:02d}'
        print(timer, end="\r")
        time.sleep(1)
        seconds -= 1
        
    print("\n⏰ 时间到！辛苦了，站起来活动一下吧！")

if __name__ == "__main__":
    # 设置一个 25 分钟的番茄钟
    pomodoro_timer(25)
