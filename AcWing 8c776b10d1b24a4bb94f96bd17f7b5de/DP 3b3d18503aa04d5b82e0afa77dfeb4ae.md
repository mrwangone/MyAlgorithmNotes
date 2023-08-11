# DP

[Knapsack Problem](DP%203b3d18503aa04d5b82e0afa77dfeb4ae/Knapsack%20Problem%20f3ea6bc787a342629b289dcce2fd1cba.md)

[线性DP](DP%203b3d18503aa04d5b82e0afa77dfeb4ae/%E7%BA%BF%E6%80%A7DP%20f12104dfdb804dc69af9e06a7ae3faed.md)

## 

## 分组背包

```cpp
for(int i=1;i<=n;i++){
      for(int j=0;j<=m;j++){
        f[i][j]=f[i-1][j];  //不选
        for(int k=0;k<s[i];k++){
          if(j>=v[i][k])     f[i][j]=max(f[i][j],f[i-1][j-v[i][k]]+w[i][k]);  
	      }
	    }
	}
	

// 优化
for (int i = 1; i <= n; i ++ )
  for (int j = m; j >= 0; j -- )
      for (int k = 0; k < s[i]; k ++ )
        if (v[i][k] <= j)
            f[j] = max(f[j], f[j - v[i][k]] + w[i][k]);
```