# Agenda
### "ag" Pairs
### Sub Arrays Intro
### Print all Subarrays
### Min and Max of Subarray


## Question 1: 

Count Pairs "ag": Given a char[N], Calculate no.of pairs = i,j such that i < j && ch[i] == 'a' && ch[j] == 'g'. All characters are lowercase

```java

Constraints:
1 <= N <= 10^5
'a' <= ch[i] <= 'g'

```

<img width="1276" alt="Screenshot 2024-12-29 at 20 59 33" src="https://github.com/user-attachments/assets/f2e229da-ed74-46bc-a110-23f285b788d9" />
<img width="1316" alt="Screenshot 2024-12-29 at 20 59 44" src="https://github.com/user-attachments/assets/4c8169fd-38e7-4f00-a69f-74f82173056b" />

## Brute Force Idea:

```java
char[] ch = {'d', 'a', 'a', 'g', 'd', 'c', 'a', 'g'};
System.out.print(coutPairs(ch));

```

```java

public static int coutPairs(char[] ch){
    int N = ch.length;
    int count = 0;
    for(int i = 0; i < N; i++){
      if(ch[i] == 'a'){
        for(int j = i + 1; j < N; j++){
          if(ch[j] == 'g'){
            count++;
          }
        }
      }
    }
    return count;
}

```

### Optimization Idea:

<img width="1316" alt="Screenshot 2024-12-30 at 08 54 44" src="https://github.com/user-attachments/assets/7f45950a-55e8-4678-8d59-661a6c7b1850" />



<img width="1289" alt="Screenshot 2024-12-30 at 09 37 34" src="https://github.com/user-attachments/assets/43697c50-261c-4b8a-9862-17e64746c2b1" />
<img width="1118" alt="Screenshot 2024-12-30 at 09 37 19" src="https://github.com/user-attachments/assets/973e19ba-e414-4a4e-9f8e-443b0005ec81" />


