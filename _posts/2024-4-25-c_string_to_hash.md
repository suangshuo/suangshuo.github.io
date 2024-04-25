---
layout : post
title : "c string to hash"
date: 2024-4-25 
tags: [everyday]
comments: true
author: suangshuo
---
众所周知，c语言的switch语句不支持char*，<br>
再加上有时候要用c实现map，有时候得用字符串检索。<br>
所以，学习char*转Hash是很重要的。
以下是一些Hash计算方法:
~~~cpp
#include <stdio.h>
unsigned int DJBHash(char *str) {
  unsigned int hash = 5381;

  while (*str) {
    hash += (hash << 5) + (*str++);
  }

  return (hash & 0x7FFFFFFF);
}
unsigned int APHash(char *str) {
  unsigned int hash = 0;
  int i;

  for (i = 0; *str; i++) {
    if ((i & 1) == 0) {
      hash ^= ((hash << 7) ^ (*str++) ^ (hash >> 3));
    } else {
      hash ^= (~((hash << 11) ^ (*str++) ^ (hash >> 5)));
    }
  }

  return (hash & 0x7FFFFFFF);
}
unsigned int BKDRHash(char *str) {
  unsigned int seed = 131; // 31 131 1313 13131 131313 etc..
  unsigned int hash = 0;

  while (*str) {
    hash = hash * seed + (*str++);
  }

  return (hash & 0x7FFFFFFF);
}
unsigned int RSHash(char *str) {
  unsigned int b = 378551;
  unsigned int a = 63689;
  unsigned int hash = 0;

  while (*str) {
    hash = hash * a + (*str++);
    a *= b;
  }

  return (hash & 0x7FFFFFFF);
}
unsigned int SDBMHash(char *str) {
  unsigned int hash = 0;

  while (*str) {
    // equivalent to: hash = 65599*hash + (*str++);
    hash = (*str++) + (hash << 6) + (hash << 16) - hash;
  }

  return (hash & 0x7FFFFFFF);
}
unsigned int ELFHash(char *str) {
  unsigned int hash = 0;
  unsigned int x = 0;

  while (*str) {
    hash = (hash << 4) + (*str++);
    if ((x = hash & 0xF0000000L) != 0) {
      hash ^= (x >> 24);
      hash &= ~x;
    }
  }

  return (hash & 0x7FFFFFFF);
}
int main() {
  char a[100];
  scanf("%s", a);
  printf("DJBHash -%d\n", DJBHash(a));
  printf("APHash  -%d\n", APHash(a));
  printf("BKDRHash-%d\n", BKDRHash(a));
  printf("RSHash  -%d\n", RSHash(a));
  printf("SDBMHash-%d\n", SDBMHash(a));
  printf("ELFHash -%d\n", ELFHash(a));

  return 0;
}
~~~
