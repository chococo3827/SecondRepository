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
void DeleteMember(){
    char str[30];
    printf("삭제할 이름 입력 : ");
    scanf("%s",str);
    for(int i=0;i<idx;i++){
        if(strcmp(arr[i].name,str) == 0){
            for(int j=i;j<idx-1;j++)
                arr[j] = arr[j+1];
            idx--;
            return;
        }
    }
    printf("삭제할 데이터가 없습니다.\n");
}
void UpdateMember(){
    char str[30];
    printf("수정할 이름 입력 : ");
    scanf("%s",str);
    for(int i=0;i<idx;i++){
        if(strcmp(arr[i].name,str) == 0){
            printf("수정을 시작합니다. ");
            printf("이름 입력 : ");
            scanf(" %s",&arr[i].name);
            
            printf("번호 입력 : ");
            scanf(" %d",&arr[i].tel);
            printf("수정 완료되었습니다.\n");
            return;
        }
    }
    printf("수정할 데이터가 없습니다.\n");
}
int main(void){
    int no = -1;

    while(no != EXIT){
        puts("--- 회원정보 관리 프로그램 ---");
        puts("1. 회원정보 등록");
        puts("2. 회원정보 검색");
        puts("3. 회원정보 삭제");
        puts("4. 회원정보 수정");
        puts("0. 프로그램 종료");
        puts("원하시는 메뉴 번호 입력 : ");
        scanf("%d",&no);

        switch(no){
            case INSERT:
                InsertMember();
                break;
            case SEARCH:
                SearchMember();
                break;
            case DELETE:
                DeleteMember();
                break;
            case UPDATE:
                UpdateMember();
                break;
        }
    }
    return 0;
}
