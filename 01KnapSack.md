![image](https://github.com/user-attachments/assets/5327257e-17a1-4139-b901-fad399b33807)

**KnapSack with recursion**

      int KnapSack(int[] wt, int[] val, int W, int n){
         1.Base Case
         if(n==0 || W==0){
           return 0;
         }
        2.Choice
         if(wt[n-1]<=W){
            Math.max(KnapSack(wt,val,W-wt[n-1],n-1),KnapSack(wt,val,W,n-1));
         }else if(wt[n-1]>W){
            KnapSack(wt,val,W,n-1);
         }
      }
      
**KnapSack with Memoization**

        int t[100][1000]           //int t[n][W], n<=100,W<=1000
      for (int i = 0; i < n; i++) {
          Arrays.fill(t[i], -1);
      }
      int KnapSack(int[] wt, int[] val, int W, int n){
         if(n==0 || W==0){
           return 0;
         }
         if(t[n][W]!=-1){
           return t[n][W];
         }
         if(wt[n-1]<=W){
           t[n][W]=Math.max(val[n+1]+KnapSack(wt,val,W-wt[n-1],n-1),KnapSack(wt,val,W,n-1));
         return t[n][W];
         }else if(wt[n-1]>W){
           return t[n][W] = KnapSack(wt,val,W,n-1);
         }
      }


**Top-Down Approach** n->i,W->j

      int[] KnapSack(int[] wt, int[] val, int W, int n){
      int t[n+1][W+1];
            for(int i=0;i<n+1;i++){
                  for(int j=0;j<W+!;j++){
                    if(i==0 || j==0){
                              t[i][j]=0;
                        }
                        if(wt[i-1]<=j){
                              t[i][j]=Math.max(val[i+1]+t[i-1][j-wt[i-1],t[i-1][j])
                        }else{
                                    t[i][j]=t[i-1][W];
                        }
                  }
            }
      }
      return t[n][W];
      }
