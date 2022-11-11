# mealmagic2022
Project in C language that attempts to build a restaurant management system
#include<stdio.h>			// Pre-processor directive (standard input output header file) 
#include<time.h> 			// header file to add current time and date
#include<stdlib.h> 			// header file to change color and clear screen after intervals when required
#include <ctype.h>			// header file mainly used for testing and mapping characters
#include <windows.h>		// header file mainly used for declarations for all of the functions 
#include<string.h>			// header file mainly used for string operations
 
typedef struct{ 			// Structure for customer's details

	char id[15]; 
	char firstname[25];
	char lastname[15];
	char number[15];
	char email[35];
	char address[70];
	char gender[8];
	char reservation[100];
	
}customer;
	
	int choice1,choice2,choice3,i,again,num,total,tables; // global variable declaration
	int x;
	char yes_no,choice;	
	
	int search(customer st[],char id[], int itemcount); // function for search and displaying main screen 
	void displayheading();
	
void titlepage(){ 				
	system("color 6"); 			// changes the color of the text
	printf("\t\t\t\t ********************************************************\n");
	printf("\t\t\t\t |\t\tWelcome to The Meal-Magic\t\t|\n");
	printf("\t\t\t\t |\tThe Ultimate Restaurant Management System\t|\n");
	printf("\t\t\t\t *********************************************************\n");
	printf("Programming Fundamentals-Project made by:\n\t Ayesha Hassan (22K-4326)\n\t Emanay Arshad (22K-4602)\n\t Muhammad Ali Ansari (22K-4135)\n\t Section: BSCS-1F\n\n"); 
	
	//For adding current date and time to the program 
    time_t time1; 				// creating time1 variable of structure time_t
    char* date_time; 			// char* = declaring a pointer to a character variable date_time 
    time(&time1); 				// using time() function to initialize time1 variable 
    date_time = ctime(&time1); // using another function ctime to display date and time in string format
    printf("Today's Date and Current Time: %s", date_time);
    
	// displaying options for the customer
	printf("\nIn this program, Pressing the following keys will perform respective actions.\n");
	printf(" 0. To exit the program\n");
	printf(" 1. Register as a new costumer\n");
	printf(" 2. Login as a registered costumer\n");
	printf(" 3. Order Meal \n");
	printf(" 4. View Customer Details \n");}
	

	
	void registration(customer st[],int *itemcount){			// function for adding customer's details 
		system("CLS");											// for clearing screen before any substitution
		printf("\t\t\tWelcome to the Registration process of The Magic Meal Restaurant.\n ");
  		printf("\t\t\t***************************************************************\n");
		again:       											// A sub-function that will be used repeatedly using "goto" (A Dev C++ Built-in function)
			printf("Enter ID: ");    							// Primary key throughout program
		  	scanf("%s",&st[*itemcount].id);
  			if(search(st,st[*itemcount].id,*itemcount)!=-1){    // If same ID already exist , display following message or else ask for further details
			printf("\nThis ID already exists\n");
			goto again;} 										// goto built function already built in 
			printf("Enter First Name: ");
			fflush(stdin);
		  	gets(st[*itemcount].firstname);
  			printf("Enter Last Name: ");
  			fflush(stdin);
  			gets(st[*itemcount].lastname);    					//using "get(s)" to include words after spaces as well 
   			printf("Enter phone number: ");
   			fflush(stdin);
   			scanf("%s",&st[*itemcount].number);
   			printf("Enter email: ");
   			fflush(stdin);
   			scanf("%s",&st[*itemcount].email);
   			printf("Enter address: ");
   			fflush(stdin);
   			gets(st[*itemcount].address);
   			printf("Enter Gender: ");
   			fflush(stdin);
   			scanf("%s",&st[*itemcount].gender);
   			printf("Enter Tables to be reserved: ");
   			fflush(stdin);
   			scanf("%s",&st[*itemcount].reservation);
   			int tables= atoi(st[*itemcount].reservation); // converting string value to integer using atoi function that is built in on <stdlib> file
   				if(tables<=0 || tables>99){ // Extreme Cases of table reservation
   					system("CLS");
   					printf("\nError in Table Reservation: Request is beyond the available tables in the restaurant\n"); 
					printf("\nOur Suggestion: Take the parcel");}
   				else if(tables>0 && tables<100){
   					printf("\nCongratulations, Your request for registration is successful.");}
   			++(*itemcount);}
			
	void login_customer(customer st[], int itemcount){ 		//function login_customer for customers who already have accounts in the database
		system("cls");	
		system("color 6");
  		printf("\t\t\t\tWe Welcome you to the login Portal of The Magic Meal Restaurant.\n ");
  		printf("\t\t\t\t*****************************************************************\n");
  		char id[10];
		printf("\n\nKindly enter your ID: ");
		scanf("%s",&id);
		int index=search(st,id,itemcount);    //making it as a parameter and equating to login_customer function to find that particular customer
		if (index != -1){
            printf("\nLogin Successfull\nWelcome Mr/Ms %s to our Restaurant.",(st[i].firstname));}
		else{
			int attempts;
			printf("\nID is incorrect or ID is not registered in the database.\n");
				for(attempts=3;attempts>0;attempts--){
					printf("\nEnter ID again: ");
					fflush(stdin);
					scanf("%s",&id);
					int index=search(st,id,itemcount);    //making it as a parameter and equating to login_customer function to find that particular customer
						if (index != -1){
                         	printf("\nLogin Successfull\nWelcome Mr/Ms %s to our Restaurant.",(st[i].firstname));}
                        else{
                        	printf(" ");}}
						}}


	int search(customer st[], char id[],int itemcount){ 		// Search function for searching Customers using ID
  	int found =-1,i;
		for (i = 0; i < itemcount && found==-1; i++){
    		if (strcmp(st[i].id,id)==0) 
				found=i;        //searching order by using ID (primary key) and comapring it with all orders
    		else 
				found=-1 ;}
		return found;
}

// Ordering Phase Starts here

	int again,total,x; 								// global variable declaration
	char choice;	
	void bfast();									// Menu functions declaration		
	void lunch();
	void dinner(); 
	void eexit();
	void m_m();
	void m_m(){ 									// main menu screen
	char choice = ' ' ; 							//local variable
	system("color 6");
  	printf("\t\t\t\tWe Welcome you to the Ordering Phase of The Magic Meal Restaurant.\n ");
  	printf("\t\t\t\t*****************************************************************\n");
  	printf("\n\nKindly enter the type of Meal you want:\n");
  	printf("\t\t\t[A] Breakfast\n");
  	printf("\t\t\t[B] Lunch\n");
  	printf("\t\t\t[C] Dinner\n");
  	printf("\t\t\t[D] Exit\n\n");
  	printf("Your Choice: ");
  	scanf("%c", &choice);
  	system("cls");{
		if (toupper(choice) == 'A' )
		  	bfast();
		else if (toupper(choice) == 'B')
			lunch();
		else if (toupper(choice) == 'C')
			dinner();
		else if (toupper(choice) == 'D'){
			printf("\nThank you for using Meal-Magic.\nWe Expect to see you again.");
			eexit;}	
		else if (toupper(choice) != 'A' , 'B' , 'C' , 'D'){ 
			m_m();}}}
						
void bfast(){ 								//Breakfast Menu Screen 
  int choice = 0;	 						//local variables
  int quantity = 0;
  int again = 0;
  fflush(stdin);
  	printf("\t\t\t\tWelcome to Ordering Phase of The Magic Meal Restaurant.\n ");
  	printf("\t\t\t\t******************************************************\n\n");
  	printf("\t\t\t\t\t*Breakfast Menu*\n");
  	printf("\nKindly enter the Meal Number of Breakfast:\n");
  	printf("\t\t\t[1] Egg & Cheese McMuffin Meal - Rs 250\n");
  	printf("\t\t\t[2] Hashbrowns Wrap with Smoothie - Rs 400\n");
  	printf("\t\t\t[3] Big Breakfast Meal - Rs 1000\n\t\t    Meal 3 includes: Three fluffy scrambled eggs, savoury chicken sausage and a crispy golden hash brown\n");
  	printf("\n\t\t\t *Special 30 %% discount on Meal 3*\n\t\t\t *Discount valid only for today*\n");
	printf("Your Choice: ");
  	scanf("%d", &choice);{
  		if (choice == 1) {
			printf("Enter quantity: ");
	  		scanf("%d", &quantity);
	  		total = 250 * quantity ;
	   		printf("Your total amount is Rs %d\nPlease pay at the counter\n\n\n ", total); 
	   		printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : "); // Allows user to choose whether to check-out or buy anything else.
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			bfast();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){
			printf("\n\nSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}
		else if ( choice == 2){
		  	printf("Enter quantity: ");
		  	scanf("%d", &quantity);
		  	total = 400 * quantity ;
		  	printf("Your total amount is Rs %d\nPlease pay at the counter\n\n\n ", total);
		    printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : "); // Allows user to choose whether to check-out or buy anything else.
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			bfast();
		else if (again == 2 )	
			m_m();
		else if (again != 1 , 2){
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}
		else if ( choice == 3 ){
			printf("Enter quantity: ");
			scanf("%d", &quantity);
			total = 700 * quantity ;
			printf("Your total amount is Rs %d\nPlease pay at the counter\n\n\n ", total); 
		    printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : "); // Allows user to choose whether to check-out or buy anything else.
			scanf("%d", &again);
			system("cls");
		if (again == 1 ){
			bfast();}
		else if (again == 2 ){	
			m_m();}
		else if (again != 1 , 2){
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}
		else if (choice != 1 , 2 , 3 ){
			fflush(stdin);
			system("cls");
			printf("\n\n\t\t   Invalid Choice Entered\n\n");
			bfast();}}}

void lunch(){ // Lunch Screen Menu
  int choice;  //local variables
  int quantity;
  int again;

  	printf("\t\t\t\tWelcome to Ordering Phase of The Magic Meal Restaurant.\n ");
  	printf("\t\t\t\t******************************************************\n\n");
  	printf("\t\t\t\t*Lunch Menu*\n");
  	printf("\nKindly enter the Meal Number of Lunch:\n");
  	printf("\t\t\t[1] Fried Rice with Fish - Rs 400\n");
  	printf("\t\t\t[2] Crispy Chicken Bucket- Rs 1600\n");
  	printf("\t\t\t[3] Happy Meal - Rs 1000\n");
  	printf("\n\t\t\t *Special 50 %% discount on Meal 2*\n\t\t\t *Discount valid only for today*\n");
	printf("Your Choice: ");
  	scanf("%d", &choice);{
  		if (choice == 1) {
	  		printf("Enter quantity: ");
	  		scanf("%d", &quantity);
	  		total = 400 * quantity ;
	  		printf("Your total amount is Rs %d \nPlease pay at the counter\n\n\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			lunch();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){	
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}}
		else if ( choice == 2){
		  	printf("Enter quantity: ");
		  	scanf("%d", &quantity);
		  	total = 800 * quantity ;
		  	printf("Your total amount is Rs %d\nPlease pay at the counter\n\n\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			lunch();
		else if (again == 2 )
				m_m();
		else if (again != 1 , 2){	
			 printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			 eexit();}}}
		else if ( choice == 3 ){
			printf("Enter quantity: ");
			scanf("%d", &quantity);
			total = 1000 * quantity ;
			printf("Your total amount is Rs %d \nPlease pay at the counter\n\n\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			lunch();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){	
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}}
		else if (choice != 1 , 2 , 3){
			fflush(stdin);
			system("cls");
			printf("\n\n\t\t Invalid Choice Entered\n\n");
			lunch();}}}
			
void dinner() {// Dinner Menu Screen
  int choice;  //local variables
  int quantity;
  int again;
    printf("\t\t\t\tWelcome to Ordering Phase of The Magic Meal Restaurant.\n ");
  	printf("\t\t\t\t******************************************************\n\n");
  	printf("\t\t\t\t*Dinner Menu*\n");
  	printf("\nKindly enter the Meal type of Dinner:\n");
  	printf("\t\t\t[1] Beef Steak - Rs 1000\n");
  	printf("\t\t\t[2] Krunch Chicken Combo - Rs 550\n");
  	printf("\t\t\t[3] Rice N Spice - Rs 300\n");
  	printf("\n\t\t\t *Special 35 %% discount on Meal 1*\n\t\t\t *Discount valid only for today*\n");
  	printf("Your Choice: ");
  	scanf("%d", &choice);{
  		if (choice == 1) {
	  		printf("Enter quantity: ");
	  		scanf("%d", &quantity);
	  		total = 650 * quantity ;
	  		printf("Your total amount is Rs %d\nPlease pay at the counter\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			dinner();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){	
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}}else if ( choice == 2){
		  	printf("Enter quantity: ");
		  	scanf("%d", &quantity);
		  	total = 550 * quantity ;
		  	printf("Your total amount is Rs %d\nPlease pay at the counter\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			dinner();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){	
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}}
		else if ( choice == 3 ){
			printf("Enter quantity: ");
			scanf("%d", &quantity);
			total = 300 * quantity ;
			printf("Your total amount is Rs %d\nPlease pay at the counter\n\n\n ", total);{
			printf("\nWould you like to buy anything else?\n[1] Yes , [2] No : ");
			scanf("%d", &again);
			system("cls");
		if (again == 1 )
			dinner();
		else if (again == 2 )
			m_m();
		else if (again != 1 , 2){	
			printf("\n\n\t\tSorry Invalid Decision Entered\n\n\n\n");
			eexit();}}}
		else if (choice != 1 , 2 , 3){
			fflush(stdin);
			system("cls");
			printf("\n\n\t\tInvalid Choice Entered\n\n");
			dinner(); }}}
void eexit()  // Exit Screen
{
  printf("\t\t\t\tThank You for using ordering phase of The Meal Magic Restaurant \n ");
  printf("\t\t\t\t*********************************\n\n");}




void viewall(customer st[], int itemcount){
	system("cls");	
	printf("\t\t\t ********************************************************\n");
	printf("\t\t\t |\t\tWelcome to The Meal-Magic\t\t|\n");
	printf("\t\t\t |\tThe Ultimate Restaurant Management System\t|\n");
	printf("\t\t\t *********************************************************\n");
	int i=0;
 		while(i<itemcount){         //loop run till n times the number of contacts addded and display all of their details in sequence they were added
   			if(st[i].id!=""){
		    	printf("\n\t\tDetails OF Customer %d",i+1);
				printf("\n\t\t**********************");
   				fflush(stdin);
   				printf("\n\nID: %s",st[i].id);
   				printf("\nFirst Name: %s",st[i].firstname);
   				printf("\nLast Name: %s",st[i].lastname);
   				printf("\nContact Number: %s",st[i].number);
   				printf("\nEmail ID: %s",st[i].email);
	   			printf("\nAddress: %s",st[i].address);
   				printf("\nGender: %s",st[i].gender);
     			printf("\nTable Reserved: %s",st[i].reservation);
				printf("\n");}
				i=i+1;
				}
system("PAUSE");}   //used to hold and stop the program temporarily until new key is pressed


int main(){
	customer st[20];
	int itemcount=0;

	titlepage();
	int yourchoice;
	char confirm;
	do{
		printf("Enter your choice(0-4): ");
		scanf("%d",&yourchoice);
		if (yourchoice==0) {
 	 		printf("\n\t\t\tThank You for using this program\n ");
  			printf("\t\t\t*********************************\n");
  			printf("\t\t\tTeam Meal-Magic expects to see you again in the near future.\n");
			printf("\t\t\t*************************************************************\n");
			break;}

switch(yourchoice){
	case 1:registration(st, &itemcount);break;
	case 2:login_customer(st,itemcount);break;
	case 4:viewall(st, itemcount);break;
	case 3:m_m();break;
default:printf("\nInvalid Input\n");    //default case
}

printf("\nPress y or Y to continue:");
fflush(stdin);
scanf("%c",&confirm);
system("CLS");
	printf("\nIn this program, Pressing the following keys will perform respective actions.\n");
	printf(" 0. To exit the program\n");
	printf(" 1. Register as a new costumer\n");
	printf(" 2. Login as a registered costumer\n");
	printf(" 3. Order Meal \n");
	printf(" 4. View Customer Details \n");}
while(confirm=='y'||confirm=='Y');
return EXIT_SUCCESS;
}
