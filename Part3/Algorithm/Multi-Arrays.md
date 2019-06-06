Multi-Arrays 多维数组

1、 声明、类型[][]
2、实例化 类型[][] a = new 类型[长度][长度];

int[][] a;
a = new int[ROW][CAL];

a[0][0] =100;
a[0][1] =200;

// 直接初始化
int[][] ={
	{1,2,3},
	{4,5,6},
	{7,8,9}
};

// 遍历
for(int i=0;i<ROW;i++){
	for(int j=0;i<CAL;j++){
		a[i][j] = i*j;  // 赋值
	}
}