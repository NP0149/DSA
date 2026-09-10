```

import java.util.*;

public class gridlex {
    static int[]rows={-1,0,1,0};
    static int[] cols={0,1,0,-1};
    static int[]door=new int[4];
    static int K;
    static int maxscore=-1;
    static long count=0;
    static void find(char arr[][],int k,int visited[][],int row,int col,int prevcoin,int score){
        visited[row][col]=1;
        if(arr[row][col]=='E'){
            if(score>maxscore){
                maxscore=score;
                count=1;
            }
            else if(score==maxscore){
                count++;
            }
            visited[row][col]=0;
            return;
        }
        for(int i=0;i<4;i++){
            int newr=row+rows[i];
            int newc=col+cols[i];
            if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]!='#' && visited[newr][newc]!=1 && k>0){
                char next=arr[newr][newc];
                if(next>='1' && next<='9'){
                    int coin=next-'0';
                    if(prevcoin==0 || coin>=prevcoin){
                        int newk=Math.min(K,k-1+coin);
                        int newscore=score+coin;
                        find(arr,newk,visited,newr,newc,coin,newscore);
                    }
                }
                else if(next>='a' && next<='d'){
                    int index=next-'a';
                    door[index]^=1;
                    find(arr,k-1,visited,newr,newc,prevcoin,score);
                    door[index]^=1;
                }
                else if(next>='A' && next<='D'){
                    int index=next-'A';
                    if(door[index]==1){
                        find(arr,k-1,visited,newr,newc,prevcoin,score);
                    }
                }
                else{
                    find(arr,k-1,visited,newr,newc,prevcoin,score);
                }
            }
        }
        visited[row][col]=0;
    }

    public static void main(String args[]){
//        char arr[][]={{'S','5','.','E'},{'3','#','#','.'},{'3','.','.','.'}};
//        char arr[][]={{'S','.','b','.'},{'4','#','B','.'},{'.','.','2','E'}};
        char arr[][]={{'S','2','4','E'}};
        K=5;
        int visited[][]=new int[arr.length][arr[0].length];
        int startrow=0;
        int startcol=0;
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                if(arr[i][j]=='S'){
                    startrow=i;
                    startcol=j;
                }
            }
        }
        find(arr,5,visited,startrow,startcol,0,0);
        if(maxscore==-1){
            System.out.println("-1 0");
        }
        else{
            System.out.println(maxscore+" "+count);
        }
    }

}
```
