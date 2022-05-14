











参数解释

```
iterable:	可迭代对象,可选

desc:		str,可选,进度条的前缀
            
total:		整数或浮点数,可选,预期的迭代次数
            
leave:		布尔,可选,如果 [default: True]，保留进度条的所有痕迹
            在迭代终止时。
            
file:		`io.TextIOWrapper` 或 `io.StringIO`,可选,指定输出进度消息的位置
            
ncols:		整数，可选
            整个输出消息的宽度。如果指定，
            动态调整进度条的大小以保持在此范围内。
            如果未指定，则尝试使用环境宽度。这
            后备是 10 米的宽度，计数器没有限制，
            统计数据。如果为 0，将不打印任何仪表（仅统计数据）。
            
mininterval:		float,可选,最小进度显示更新间隔 [默认值：0.1] 秒。
            
maxinterval:		float,可选,最大进度显示更新间隔 [默认值：10] 秒。
                    自动调整`miniters`以对应`mininterval`
                    经过长时间的显示更新滞后。仅在 `dynamic_miniters` 时有效
                    或启用监控线程。
            
miniters:		int 或 float,可选
                最小进度显示更新间隔，以迭代为单位。
                如果为 0 和 `dynamic_miniters`，会自动调整为相等
                `mininterval`（CPU 效率更高，适用于紧密循环）。
                如果 > 0，将跳过指定迭代次数的显示。
                调整这个和 `mininterval` 以获得非常有效的循环。
                如果您的进度在快速和慢速迭代中都不稳定
                （网络，跳过项目等）你应该设置 miniters=1。
            
ascii:			bool 或 str,可选
                如果未指定或为 False，则使用 unicode（平滑块）填充
                仪表。回退是使用 ASCII 字符“123456789#”。
            
disable:		布尔值,可选
                是否禁用整个进度条包装器
                [默认值：假]。如果设置为无，则在非 TTY 上禁用。
            
unit:		str,可选
            将用于定义每次迭代的单元的字符串
            [默认：它]。
            
unit_scale:		bool 或 int 或 float，可选
                如果为 1 或 True，迭代次数将减少/缩放
                自动和一个公制前缀
                将添加国际单位制标准
                （千、兆等）[默认值：假]。如果任何其他非零
                数字，将缩放 `total` 和 `n`。
            
dynamic_ncols:	bool，可选
                如果设置，则不断将 `ncols` 和 `nrows` 更改为
                环境（允许调整窗口大小）[默认值：False]。
            
smoothing:		浮动，可选
                速度估计的指数移动平均平滑因子
                （在 GUI 模式下被忽略）。范围从 0（平均速度）到 1
                （当前/瞬时速度）[默认值：0.3]。
            
bar_format:		str，可选
                指定自定义条形字符串格式。可能会影响性能。
                [默认值：'{l_bar}{bar}{r_bar}']，其中
                l_bar='{desc}：{百分比：3.0f}%|'和
                r_bar='| {n_fmt}/{total_fmt} [{elapsed}<{remaining}, '
                  '{rate_fmt}{postfix}]'
                可能的变量：l_bar、bar、r_bar、n、n_fmt、total、total_fmt、
                  百分比，经过，经过_s，ncols，nrows，desc，单位，
                  速率，rate_fmt，rate_noinv，rate_noinv_fmt，
                  rate_inv, rate_inv_fmt, 后缀, unit_divisor,
                  剩余，剩余_s，等。
                请注意，在 {desc} 之后会自动删除结尾的“:”
                如果后者为空。
            
initial:	int或float，可选
            初始计数器值。重新启动进度时很有用
            栏 [默认值：0]。如果使用浮点数，请考虑指定 `{n:.3f}`
            或 `bar_format` 中的类似内容，或指定 `unit_scale`。
            
position:	int，可选
            指定打印此条的行偏移量（从 0 开始）
            如果未指定则自动。
            用于一次管理多个条形图（例如，从线程）。
            
postfix:	dict或*，可选
        	指定要在栏末尾显示的其他统计信息。
            如果可能，调用 `set_postfix(**postfix)` (dict)。
            
unit_divisor:		浮点数，可选
            		[默认值：1000]，除非 `unit_scale` 为 True，否则忽略。
            
write_bytes:	布尔值，可选
                如果（默认值：无）并且 `file` 未指定，
                字节将在 Python 2 中写入。如果 `True` 也将写入
                字节。在所有其他情况下将默认为 unicode。
            
lock_args:		元组，可选
                传递给 `refresh` 以获取中间输出
                （初始化、迭代和更新）。
            
nrows:		整数，可选
            屏幕高度。如果指定，则隐藏此之外的嵌套条
            边界。如果未指定，则尝试使用环境高度。
            后备是 20。
            
colour:		str，可选
            条形颜色（例如“绿色”、“#00ff00”）。
            
delay:		浮动，可选
            在 [default: 0] 秒过去之前不显示。
            
gui:		bool，可选
            警告：内部参数 - 不要使用。
            使用 tqdm.gui.tqdm(...) 代替。如果设置，将尝试使用
            用于图形输出的 matplotlib 动画 [默认值：False]。
```



示例

手动更新

```python
import time
from tqdm import tqdm, trange

pbar = tqdm(total=100)
for i in range(10):
    # 设置进度条左边的描述
    pbar.set_description("epoch")
    # 设置进度条右边的描述
    pbar.set_postfix_str('loss={}'.format(i))
    # 休眠 1 秒
    time.sleep(1)
    # 手动更新进度条
    pbar.update(10)
# 关闭资源
pbar.close()
```

使用上下文对象

```python
import time
from tqdm import tqdm, trange

pbar = tqdm(total=100)
with pbar:
    for i in range(10):
        # 设置进度条左边的描述
        pbar.set_description("epoch")
        # 设置进度条右边的描述
        pbar.set_postfix_str('loss={}'.format(i))
        # 休眠 1 秒
        time.sleep(1)
        # 手动更新进度条
        pbar.update(10)
```

