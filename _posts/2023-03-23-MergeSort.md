---
bg: "code.jpg"
layout: post
title:  "Merge Sort in Java"
crawlertitle: "JAEHYUNLOG"
summary: "컴퓨터알고리즘 3주차"
date:   2023-03-23 19:17:00
categories: posts
tags: 'Algorithm'
author: Jaehyun
---
# Merge Sort

Merge Sort (병합/합병 정렬) 을 사용하는 이유
: Merge Sort는 Binary Tree의 형태로 쪼개기 때문에 최대 깊이는 log n이 된다.
이때, 각 분할별로 합병을 진행하기 때문에 총 시간복잡도는 O(nlogn)이 된다.

Merge Sort의 코드는 다음과 같다.
* * *

```
public class Mergesort {
    public static int[] A;  //배열 선언
    public static int[] tmp; //임시 저장할 배열 선언

    public static void main(String[] args) {
        A = new int[]{37, 10, 22, 30, 35, 13, 25, 24};
        tmp = new int[A.length];    //배열 속에 아무것도 없고, 크기는 A만큼 가짐
        System.out.println(A.length);
        PrintArray(A);  // MergeSort 전 배열의 내용 출력
        MergeSort(0, A.length-1);
        PrintArray(A);

    }

    public static void MergeSort(int start, int end)
    {
        if(start<end)
        {
            int mid = (start + end)/2;
            MergeSort(start, mid);
            MergeSort(mid+1, end);

            int left = start;
            int right = mid+1;
            int idx = left;

            while(left <= mid || right <= end) {
                if(right>end || (left<=mid && A[left]<A[right])) {   // 나눠진 오른쪽 배열이 끝나거나, 배열의 왼쪽이 오른쪽보다 작을 때
                    tmp[idx++] = A[left++]; //임시 저장 배열에 A의 왼쪽 배열 숫자를 저장하고 idx와 left의 값을 1씩 추가한다.
                }
                else tmp[idx++] = A[right++]; //배열의 오른쪽이 왼쪽보다 작을 때, 임시 저장 배열에 오른쪽 배열 숫자를 저장한다.
            }
            for(int i=0; i<=end; i++)
                A[i]=tmp[i];
        }
    }

    public static void PrintArray(int[] a)  //배열을 출력하는 기능
    {
        for(int i = 0; i < a.length; i++) {
            System.out.print(a[i] + " ");
        }
        System.out.println();
    }
}
```

`실행 결과
8

37 10 22 30 35 13 25 24 

10 13 22 24 25 30 35 37
`
* * *
