# 2021-04-18
指针训练！

1、按如下函数原型，采用梯形法编程实现，在积分区间[a,b]内划分n个小区间，这里取n=100，
计算函数y1=∫10(1+x2)dx和y2=∫30x1+x2dx的定积分。其中，指向函数的指针变量f用于接收被积函数的入口地址。
Integral(float (*f)(float), float a, float b);
**输出格式要求："y1=%f\ny2=%f\n"

答案：
#include<stdio.h>

float Func1(float x);
float Func2(float x);
float Integral(float (*f)(float), float a, float b);

int main(int argc,char const *argv[])
{
	float y1,y2;
	y1 = Integral(Func1,0.0,1.0);
	y2 = Integral(Func2,0.0,3.0);
	printf("y1=%f\ny2=%f\n",y1,y2);
    return 0; 
}
//函数功能：计算函数 1 + x * x的值 
float Func1(float x)
{
	return 1 + x * x;
}
//函数功能：计算函数 x / (1 + x * x)的值
float Func2(float x)
{
	return x / (1 + x * x);
}

float Integral(float (*f)(float), float a, float b)
{
	float s,h;
	int n = 100,i;
	s = ((*f)(a) + (*f)(b)) / 2;
	h = (b - a) / n;
	for (i=1 ; i<n ; i++)
	{
		s += (*f)(a + i * h);
	}
	return s*h;
}
总结：函数入口地址即为函数名。
