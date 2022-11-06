# Software-Development-Capstone-Project
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <conio.h>
#include <windows.h>
void coordinate(int x, int y)
{
    COORD CRD;
    CRD.X= x;
    CRD.Y= y;
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE),CRD);

}

struct user
{
    char first_name[32];
    char last_name[32];
    char name[64];
    char ID[16];
    char number[16];
    char email[32];
    char user_name[32];
    char password[32];
};
typedef struct user Suser;
login()
{
    char username[30],password[20];
    FILE *data;
    data=fopen("data.txt","r");
    Suser log;

    coordinate(15,10);
    printf("\nPlease Enter your login credentials below\n\n");
    printf("Username:  ");
    scanf("%s",&username);
    printf("\nPassword: ");
    printf("\n");
    scanf("%s",&password);

    while(fread(&log,sizeof(log),1,data))
        {
        if(strcmp(username,log.user_name)==0 && strcmp(password,log.password)==0)

            {
                printf("\nSuccessful Login\n");
            }
        else
            {
                printf("\nIncorrect Login Details\nPlease enter the correct credentials\n");
            }
}

fclose(data);

}
create_profile()
{
    char name[15];
    FILE *data;
    data=fopen("data.txt","w");
    Suser create;

    coordinate(15,5);

    printf("\nWelcome to your online course provider. We need to enter some details for registration.\n\n");
    printf("\nEnter First Name:");
    scanf("%s",create.first_name);
    printf("\nEnter Surname:");
    scanf(" %s",create.last_name);
    printf("\nEnter your ID:");
    scanf("%s",create.ID);
    printf("\nEnter Your Mobile Number: ");
    scanf("%s",create.number);
    printf("\nEnter Your E-mail Address: ");
    scanf("%s",create.email);

    getchar();
    system("CLS");

    coordinate(15,5);

    printf("\n\n\n\t Your Information: \n\n\n");

    int i=0, j=0, length=0;
    while(create.first_name[i]!='\0')
    {
        i++;
        length++;
    }
    while(create.last_name[j]!='\0')
    {
        create.first_name[length+j] = create.last_name[j+1];
        j++;
    }
    printf("\n\n\n\tName: %s\n",create.first_name);
    printf("\n\n\tID: %s\n",create.ID);
    printf("\n\n\tMobile Number: %s\n",create.number);
    printf("\n\n\tEmail: %s\n",create.email);

    printf("\nPress Enter Key to Confirm details...\n\n\n");
    getchar();
    system("CLS");

    coordinate(15,5);

    printf("\n\n\nWelcome");
    printf("\n\n\n\tSet Username & Password: ");
    printf("\nEnter Username:\n");
    scanf("%s",create.user_name);
    printf("\nEnter Password:\n");
    scanf("%s",create.password);

    fwrite(&create,sizeof(create),1,data);
    fclose(data);

    printf("\nRegistration Successful!\n");
    printf("Press 'ENTER' key to continue...");
        getchar();
    system("CLS");

    main();
    //login();
}


int main(){
    system("COLOR 70");
    int option;
    coordinate(15,10);
    printf("Choose Your option:  \n 1. Register \n 2. Log In\n");
    scanf("%d",&option);
    if(option == 1)
        {
            system("CLS");
            create_profile();
        }
    else if(option == 2)
        {
            system("CLS");
            login();
        }
}
