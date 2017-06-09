**2017.06.09**

## ffmpeg图片合成帧动画视频

```
# 图片计数
x=0

# 删除输出目录，重建
rm -rf $1/output
mkdir $1/output

# 遍历脚本第1个参数，表示图片资源目录，遍历目录里的jpg
for i in $1/*.jpg
do
# x计数器自增
x=`expr $x + 1`
# 设定3位数长度的数字
num=$((1000+$x))
# 截掉开头的1，保持数字都是3位
num=${num:1}

# 图片改名复制到output
echo ./$i ./$1/output/image$num.jpg
cp "${i}" ./$1/output/image$num.jpg
done

# 图片合成视频
ffmpeg -y -r 10 -i ./$1/output/image%3d.jpg ./$1/output/output.mp4

# 删除输出目录的图片
rm -rf ./$1/output/*.jpg



```



