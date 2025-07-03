# Activity 4: C ya!

### July 3, 2025

### Skiers (John Chin, Bowen Huang)

### 1. Add the missing code

```
#include <stdio.h>
#include <math.h>

int main(int argc, char *argv[])
{
  int width=24,
  		length=11;

  // print out the area of the box defined by width and length
  // it should look like
  // 		A box of width #### and length #### has an area of ####.

  // calculate the length of a diagonal (hint: think Pythagoras)
  // and print it with two decimal places

}
```

### 2. Fix it

```
#include <stdio.h>

int main()
{
    int a = 2;

    if (a == 2) {
                    printf("value of a is %d\n", a);
        a++;
    }
    else {
      printf("value of a is not equal to 2.\n ");
    }

    return 0;
}

```

### 3. Even or Odd

```
#include <stdio.h>
#include <string.h>
int main(int argc, char *argv[])
{
  int temp=0, odd=0;
  char answer[5];
  if (argc==2) {
    if (1==sscanf(argv[1], "%d", &temp)) {
     odd = temp % 2;
     if (odd) {
        strncpy(answer,"Odd", sizeof(answer));
      }
      else {
        strncpy(answer, "Even", sizeof(answer));
      }
      puts(answer);
      return(0);
    }
  }
	else {
  	fprintf(stderr,"Usage: %s num , where num is an integer\n", argv[0]);
  	return 1;
	}
}
```

### 4. Produce the sum of integers

```
include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  int sum=0, max=0;
  if (argc==2) {
    if (1==sscanf(argv[1], "%d", &max)) {

                        // make sure the max is valid (i.e. a number btw 1 < x < 100)
      if (max > 1 && max < 100) {
        printf("moving on to loop\n");
      } else {
        printf("usage %s [max]; your max is out of range\n", argv[0]);
        exit(1);
      }
      // use a loop to calculate the sum
      int counter = 1;

      while (counter <= max) {
        sum += counter;
        counter += 1;
      }

                // display the answer

      printf("The cumulative sum is: %d\n", sum);
    }
    else {
      // user entered a non-number, so issue error message and exit
      printf("usage %s; you entered a non-number.\n", argv[0]);
      exit(2);
    }
  }
        else {
        fprintf(stderr,"Usage: %s num , where num is an integer\n", argv[0]);
        return 1;
        }
}
```

### 5. Leap Year

```
#include <stdio.h>
int main(int argc, char *argv[])
{
    int year = 0;
    int leap = 0;
    if (argc == 2) {
        if (1 == sscanf(argv[1], "%d", &year)) {
            if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
                leap = 1;
            }
            if (leap) {
                printf("%d is a leap year.\n", year);
            } else {
                printf("%d is NOT a leap year.\n", year);
            }
            return 0;
        }
    }
    fprintf(stderr, "Usage: %s year\n", argv[0]);
    return 1;
}
```

### 6. How big is it

```
#include <stdio.h>


int main(int argc, char *argv[])
{
    printf("Size of char: %zu bytes\n", sizeof(char));
    printf("Size of int: %zu bytes\n", sizeof(int));
    printf("Size of short: %zu bytes\n", sizeof(short));
    printf("Size of long: %zu bytes\n", sizeof(long));
    printf("Size of float: %zu bytes\n", sizeof(float));
    printf("Size of double: %zu bytes\n", sizeof(double));
    return 0;
}
```

Extra - when I copied this code and compiled it on my local machine, I still got the same results:  
Size of char: 1 bytes  
Size of int: 4 bytes  
Size of short: 2 bytes  
Size of long: 8 bytes  
Size of float: 4 bytes  
Size of double: 8 bytes

### 7. Print a half-period

```
#include <stdio.h>
#include <stdlib.h>
int main(int argc, char *argv[])
{
    int n, i, j;
    if (argc != 2) {
        fprintf(stderr, "Usage: %s number\n", argv[0]);
        return 1;
    }
    n = atoi(argv[1]);
    for (i = 1; i <= n; i++) {
        for (j = 1; j <= i; j++) {
            printf("%d ", i);
        }
        printf("\n");
    }
    return 0;
}
```
