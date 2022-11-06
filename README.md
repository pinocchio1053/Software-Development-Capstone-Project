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
                printf("Please have Patience! We are developing the site!");
                break;
            }
        else
            {
                printf("\nIncorrect Login Details\nPlease enter the correct credentials\n");
                login();
                break;
            }
}
fclose(data);
}
create_profile(){
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

    while(create.first_name[length]!='\0'){
        ++length;
    }
    for(i=0; create.last_name[i]!= '\0'; ++i, ++length){
        create.first_name[length]= create.last_name[i];
    }
            create.first_name[length]= '\0';

    printf("\n\n\nName: ");
    puts(create.first_name);
    printf("\n\n\tID: %s\n",create.ID);
    printf("\n\n\tMobile Number: %s\n",create.number);
    printf("\n\n\tEmail: %s\n",create.email);

    system("CLS");
    coordinate(15,10);
    int option;
    printf("Enter 1 to Save info or 2 to Cancel: ");
    scanf("%d",&option);

    if(option==1)
    {
        getchar();
    system("CLS");
    coordinate(15,5);

    printf("\n\n\nWelcome %s! Your information have been Saved!",create.first_name);
    printf("\n\n\n\tSet Username & Password: ");
    printf("\n\nEnter Username:\n");
    scanf("%s",create.user_name);
    printf("\nEnter Password:\n");
    scanf("%s",create.password);

    fwrite(&create,sizeof(create),1,data);
    fclose(data);

    printf("\nRegistration Successful!\n");
    printf("Press 'ENTER' key to continue...");
    }
    else if(option==2)
    {
        getchar();
    system("CLS");
    coordinate(15,10);
    main();
    }
    else
        printf("Wrong Choice!");
   system("CLS");
   coordinate(15,10);
    int choice;
    printf("Enter 1 to go to 'Main Menu' or Enter 2 to go to 'Login'\n\n");
    scanf("%d",&choice);
    if(choice==1)
    {
        getchar();
    system("CLS");
    coordinate(15,10);
    main();
    }
    if(choice==20)
       {
           getchar();
    system("CLS");
    coordinate(15,10);
    login();
       }
}
int main(){
    system("COLOR 70");
    int choice,option;
    coordinate(15,10);
    printf("Choose Your option:  \n 1. User \n 2. Admin\n\n");
    scanf("%d",&choice);
            system("CLS");

            coordinate(15,10);
    switch(choice)
    {
    case 1:
        printf("Choose Your Option: \n\n 1. Create Profile \n 2. Log in\n\n");
        scanf("%d",&option);
        switch(option)
        {
        case 1:
             {
            system("CLS");
            create_profile();
        }
        break;
        case 2:
            {
                 {
            system("CLS");
            login();
        }
            }
            break;
        }
        break;
        case 2:
            {
                printf("Admin Access is Under Development\n\n");
                int back;
                printf("Choose 1 to go back or Press Any Key to EXIT!\n");
                scanf("%d",&back);
                switch(back)
                {
                case 1:
                    {
                        system("CLS");
                        coordinate(15,10);
                    main();
                    }
                default:
                    return 0;
                }
            break;
            }
        default:
            printf("Wrong Option!");
        }
    }
