## iOS 的一些简单的技术方案
`代码未优化，将想法直面呈现，若有bug或者更好的方案，欢迎提出`

1.将一个数字拆分，相乘的结果再次相乘,直到结果是个位数->结束
>  如：153--拆分--相乘--> 1x5x3 = 15 --拆分--相乘--> 1x5 = 5 结束

代码示例

```objective-c
NSString *num = @"153";
//    1*5*3 = 15;
//    1*5 = 5;
NSMutableArray *muArray = [NSMutableArray array];

NSInteger all = 1;
BOOL isdo = NO;
while (num.length > 1) {
    for (id tempa in muArray ) {
        isdo = YES;
        all = all*[tempa integerValue];
    }
    if (isdo) {
        NSLog(@"all:%ld",(long)all);
        isdo = NO;
        num = [NSString stringWithFormat:@"%ld",(long)all];
        all = 1;
    }
    [muArray removeAllObjects];
    for (int i =0; i < num.length; i++) {
        NSString *temps = [num substringWithRange:NSMakeRange(i, 1) ];
        [muArray addObject:temps];
    }
}
```
all:15
all:5
