# GLEBKREPP
#include "pch.h"
#include <iostream>

int main()
{
	int n,m,r,temp,c=0, *y, sum = 0, **x;
	printf("Enter the num of rows and cols: \n");
	scanf_s("%d%d", &n,&m);
	y = (int *)malloc(m * sizeof(int));
	x = (int **)malloc(n * sizeof(int));
	for (int i = 0; i < n; i++)
	{
		x[i] = (int *)malloc(m * sizeof(int));
	}
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < m; j++)
		{
			printf("Enter the %d %d element of array: \n", i + 1, j + 1);
			scanf_s("%d", &x[i][j]);
		}
	}
	x = (int **)realloc(x, (n + 1) * sizeof(int));
	x[n] = (int *)malloc(m * sizeof(int));
	r = n / 2;
	for (int j = 0; j < m; j++)
	{
		sum = 0;
		c = 0;
		for (int i = 0; i < n; i++)
		{
			sum += x[i][j];
			c++;
		}
		y[j] = sum/c;
	}
	for (int j = 0; j < m; j++)
	{
		for (int i = n; i >r; i--)
		{
			temp = x[i - 1][j];
			x[i][j] = x[i - 1][j];
			x[i - 1][j] = temp;
		}
	}
	for (int j = 0; j < m; j++)
	{
		x[r][j] = y[j];
	}
	for (int i = 0; i < n+1; i++)
	{
		for (int j = 0; j < m; j++)
		{
			printf("%d ", x[i][j]);
		}
		printf("\n");
	}
}
