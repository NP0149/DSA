```
import java.util.*;
public class treasure_hunter {
    static int rows[]={-1,0,1,0};
    static int cols[]={0,1,0,-1};
    static int alpha[]={0,0,0,0};
    static int maxscore=0;
    static int count=0;
    static int find(char arr[][],int k,int visited[][],int src[],int dest[],int row,int col,int prev){
        visited[row][col]=1;
        if(arr[row][col]=='E'){
            return 1;
        }
        for(int i=0;i<4;i++){
            int newr=row+rows[i];
            int newc=col+cols[i];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]!='#' && k>0 && visited[newr][newc]!=1){
                if(arr[newr][newc]>='a' && arr[newr][newc]<='d'){
                    alpha[arr[newr][newc]-'a']=1;
                   count+= find(arr,k-1,visited,src,dest,newr,newc,prev);
                }
                else if(arr[newr][newc]>='A' && arr[newr][newc]<='D'){
                    if(alpha[arr[newr][newc]-'A']==1){
                       count+= find(arr,k-1,visited,src,dest,newr,newc,prev);
                    }
                }
                else if(arr[newr][newc]>='1' && arr[newr][newc]<='9'){
                    int num=arr[newr][newc]-'0';
                    if(prev==0 || num>=prev){
                        maxscore+=num;
                        int newk=Math.min(k,k-1+num);
                        count+= find(arr,newk,visited,src,dest,newr,newc,num);
                    }
                }
                else{
                   count+= find(arr,k-1,visited,src,dest,newr,newc,prev);
                }
            }
        }
        if(arr[row][col]>='a' && arr[row][col]<='d') {
            alpha[arr[row][col] - 'a'] = 0;
        }
        visited[row][col]=0;
       return 0;
    }

    public static void main(String args[]){
        char arr[][]={{'S','5','.','E'},{'3','#','#','.'},{'3','.','.','.'}};
        int k=5;
       int visited[][]=new int[arr.length][arr[0].length];
       int src[]=new int[2];
       int dest[]=new int[2];
       for(int i=0;i<arr.length;i++){
           for(int j=0;j<arr[0].length;j++){
               if(arr[i][j]=='S'){
                   src[0]=i;
                   src[1]=j;
               }
               if(arr[i][j]=='E'){
                   dest[0]=i;
                   dest[1]=j;
               }
           }
       }
        find(arr,k,visited,src,dest,src[0],src[1],0);
        System.out.println(maxscore);
        System.out.println(count);
    }

}
```
