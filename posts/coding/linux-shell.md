Linux Shell 开发
===============

## 变量

内置变量

```
$? 返回值
$# 参数数量
$@ 参数列表
$$ 当前 PID
```

## 逻辑运算

### 字符串逻辑运算
```shell
if [ "$str1" = "$str2" ]; then
    echo "字符串相等"
fi

if [ "$str1" != "$str2" ]; then
    echo "字符串不相等"
fi

if [ -z "$str1" ]; then
    echo "字符串为空"
fi

if [ -n "$str1" ]; then
    echo "字符串非空"
fi
```

### 文件逻辑运算

if [ -e "$path" ]; then
    echo "路径存在"
fi

if [ -d "$dir" ]; then
    echo "目录存在"
fi

## 流控

## 数组

数组创建 访问

创建
```
# 定义数组并赋值
arr=(value1 value2 value3)

arr=()  # 定义空数组

arr[0]="value1"
arr[1]="value2"
arr[2]="value3"
```

访问
```
echo ${arr[0]}  # 输出第一个元素 value1

echo ${arr[@]}  # 输出整个数组的所有元素

echo ${arr[*]}  # 也输出整个数组的所有元素

echo ${#arr[@]}  # 输出数组元素的数量

# 循环遍历数组
for item in "${arr[@]}"; do
    echo "$item"
done

```

修改数组元素
```
arr[1]="new_value"  # 修改第二个元素
```

删除数组元素
```
unset arr[1]  # 删除数组中的第二个元素

unset arr  # 删除整个数组

```

> [@] 和 [*] 的区别：
> 
> ```"${arr[@]}"``` 和 ```"${arr[*]}"``` 在循环时表现不同。
>
> * ```[@]``` 可以保留每个元素的独立性，适合于处理元素包含空格的情况。
> * ```[*]``` 会将所有元素作为一个单一的字符串处理，空格会连接所有元素。
>
> 空格问题: 在引用数组元素时，使用双引号 "${arr[@]}" 避免空格或特殊字符引发的问题。

## 字符处理

### 字符串长度

可以通过 ```${#string}``` 来获取字符串的长度。

```shell
str="Hello, World!"
echo ${#str}  # 输出字符串的长度 13
```

### 字符串截取

使用 ```${string:position:length}``` 语法来截取字符串：

* ```position``` 是起始位置（从 0 开始）。
* ```length``` 是截取的长度（可选，如果不指定长度，默认从起始位置到字符串的末尾）。

```shell
str="Hello, World!"
echo ${str:7}      # 输出 "World!"（从位置7开始到结尾）
echo ${str:0:5}    # 输出 "Hello"（从位置0开始，截取5个字符）
```

字符串替换

使用 ```${string/old/new}``` 来替换字符串中的内容：

* ```${string/old/new}```: 替换第一个匹配项。
* ```${string//old/new}```: 替换所有匹配项。
* ```${string/old}```: 删除匹配项。

```shell
str="Hello, World!"
echo ${str/World/Bash}   # 输出 "Hello, Bash!"（替换第一个匹配）
echo ${str//o/O}         # 输出 "HellO, WOrld!"（替换所有匹配）
echo ${str/Hello/}       # 输出 ", World!"（删除 "Hello" 部分）

```

### 字符串查找

通过 expr 或 [[ ... ]] 来查找字符串中的子串。


使用 expr 查找子串的位置：
```shell
str="Hello, World!"
position=$(expr index "$str" "o")  # 查找字符 "o" 的位置
echo $position  # 输出 5（"o" 在字符串中的位置）
```

使用 [[ ... ]] 查找字符串是否包含某个子串：
```shell
str="Hello, World!"
if [[ "$str" == *"World"* ]]; then
    echo "Found 'World' in the string!"
fi
```

### 字符串大小写转换

可以使用 ```tr``` 或 ```${string^^}```、```${string,,}``` 来进行大小写转换。

```
str="hello"
echo ${str^^}  # 输出 "HELLO"

str="HELLO"
echo ${str,,}  # 输出 "hello"

echo "hello" | tr 'a-z' 'A-Z'  # 输出 "HELLO"
echo "HELLO" | tr 'A-Z' 'a-z'  # 输出 "hello"
```

### 删除字符
使用 tr 删除字符串中的特定字符。
```shell
str="hello, world!"
echo $str | tr -d 'l'  # 输出 "heo, word!"

```

### 字符串拆分

通过 ```IFS``` (Internal Field Separator) 可以对字符串进行拆分。

基于空格拆分：
```shell
str="apple orange banana"
IFS=' ' read -r -a arr <<< "$str"
for word in "${arr[@]}"; do
    echo $word
done
```

基于自定义分隔符拆分：
```shell
str="apple,orange,banana"
IFS=',' read -r -a arr <<< "$str"
for word in "${arr[@]}"; do
    echo $word
done
```

## 计算

### 整数计算

使用```$((expr))```进行算术运算

这是最常用的整数计算方式，它支持加、减、乘、除、取余等基本操作。
```shell
# 加法
a=5
b=3
sum=$((a + b))
echo "Sum: $sum"  # 输出 "Sum: 8"

# 减法
diff=$((a - b))
echo "Difference: $diff"  # 输出 "Difference: 2"

# 乘法
product=$((a * b))
echo "Product: $product"  # 输出 "Product: 15"

# 除法
quotient=$((a / b))
echo "Quotient: $quotient"  # 输出 "Quotient: 1"

# 取余
remainder=$((a % b))
echo "Remainder: $remainder"  # 输出 "Remainder: 2"

```

使用 expr 进行计算
expr 也是一个常用的工具，但它要求在运算符两边加空格。
```shell
a=5
b=3

sum=$(expr $a + $b)
echo "Sum using expr: $sum"  # 输出 "Sum using expr: 8"

product=$(expr $a \* $b)
echo "Product using expr: $product"  # 输出 "Product using expr: 15"
```

> 注意：expr 使用时，乘法操作符 * 需要转义为 \*，因为 * 是 Shell 的通配符。

### 浮点数计算

> Shell 默认只支持整数运算，但可以使用 bc 工具来进行浮点数运算。

#### 使用 bc 进行浮点数计算

```shell
# 定义浮点数并进行运算
a=5.5
b=2.3

# 使用 bc 进行加法运算
sum=$(echo "$a + $b" | bc)
echo "Sum of float numbers: $sum"  # 输出 "Sum of float numbers: 7.8"

# 限制小数点后位数
sum=$(echo "scale=2; $a + $b" | bc)
echo "Sum with scale 2: $sum"  # 输出 "Sum with scale 2: 7.80"

# 浮点数乘法
product=$(echo "$a * $b" | bc)
echo "Product of float numbers: $product"  # 输出 "Product of float numbers: 12.65"
```

##### 设置 scale 进行精度控制
```scale``` 控制 ```bc``` 运算结果的精度。例如，```scale=2``` 表示保留两位小数。

```shell
# 限制浮点数计算的结果精度
result=$(echo "scale=2; 10 / 3" | bc)
echo "Result of division with 2 decimal places: $result"  # 输出 "Result of division with 2 decimal places: 3.33"
```

#### 使用 awk 进行计算

```awk``` 是一个强大的文本处理工具，也可以用于数学计算，支持浮点数和复杂的表达式。
```shell
# 使用 awk 进行浮点数运算
a=5.5
b=2.3
echo | awk "{print $a + $b}"  # 输出 "7.8"

# 使用 awk 进行更复杂的运算
echo | awk "{print ($a + $b) * 2}"  # 输出 "15.6"
```


## 重定向

流重定向

```shell
ls > dirlist 2>&1
```

### 重定向 stdout & stderr
```shell
&>word

# or 

>&word 
```

第一种等价于
```shell
>word 2>&1
```

#### 使用 exec 重定向文件描述符

通过 ```exec```，你可以重定向标准输入、标准输出、标准错误等流。特别地，```exec``` 可以更灵活地控制文件描述符的打开和关闭。

##### 标准输出重定向
```shell
exec > output.txt  # 将标准输出重定向到 output.txt
echo "This will go to output.txt"  # 输出内容将写入 output.txt 文件
```
执行上述命令后，所有的标准输出（echo、命令输出等）都将重定向到 output.txt 文件中。

##### 标准错误输出重定向
```shell
exec 2> error.log  # 将标准错误输出重定向到 error.log
ls non_existing_file  # 错误信息将写入 error.log 文件
```
这条命令将标准错误（stderr）重定向到 error.log 文件中。如果 ls 命令找不到文件，将会把错误信息写入 error.log。

##### 同时重定向标准输出和标准错误
```shell
exec > output.txt 2>&1  # 同时将标准输出和标准错误输出重定向到 output.txt
echo "This is a normal output"
ls non_existing_file  # 正常输出和错误输出都会写入 output.txt 文件
```
在这条命令中，exec > output.txt 会重定向标准输出，而 2>&1 将标准错误重定向到标准输出。这样，两个流都将被写入 output.txt 文件。


##### 关闭文件描述符

```exec``` 也可以用于关闭文件描述符。例如，关闭标准输出：

```shell
exec 1>&-  # 关闭标准输出
echo "This won't be displayed on the screen"  # 此输出不会显示在屏幕上
```
这条命令通过 exec 关闭了文件描述符 1（标准输出）。因此，后续的 echo 命令不会显示在屏幕上。

##### 重定向文件描述符
```shell
exec 3> file.txt  # 打开文件描述符 3 并将其指向 file.txt
echo "This will go to file.txt" >&3  # 将内容写入文件描述符 3
exec 3>&-  # 关闭文件描述符 3
```
这条命令通过 ```exec``` 打开文件描述符 3，并将其重定向到 ```file.txt```。然后使用 ```echo``` 将内容写入文件描述符 3 所指向的文件。最后，```exec 3>&-``` 关闭文件描述符 3。