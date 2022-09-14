# SecondRepository
#include <stdio.h>
#include <string.h>

enum {
    EXIT,
    INSERT,
    SEARCH,
    DELETE,
    UPDATE
};
typedef struct member{
    char name[30];
    int tel;
}Member;
Member arr[20] ={};
int idx = 3; 
void InsertMember(){
    if(idx == 20){
        printf("더이상 저장할 공간이 없습니다\n");
        return;
    }
    printf("이름 입력 : ");
    scanf(" %s",arr[idx].name);
    printf("번호 입력 : ");
    scanf(" %d",&arr[idx].tel);
    idx++;
    printf("회원정보 등록 완료\n");
}
void SearchMember(){
    char str[30];
    printf("검색할 이름 입력 : ");
    scanf("%s",str);
    for(int i=0;i<idx;i++){
        if(strcmp(arr[i].name,str) == 0){
            printf("%s %d %c\n",arr[i].name, arr[i].tel);  
            return;
        }
    }
    printf("검색 결과가 없습니다.\n");
}
