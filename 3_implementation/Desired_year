#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define TILDA '~'
#define TWO 2
#define MAX 63
#define DAYSOFWEEK 7
#define TEN 10
#define FOURHUNDRED 400
#define ONEHUNDRED 100
#define FOUR 4

int calculateDayZero(int year)
{
	int result;
	result = (((year - 1) * 365) + ((year - 1) / 4) - ((year - 1) / 100) +
	((year) / 400) + 1) % 7;
	return result;
}

void printTilda(int total)
{
	for(int i = 0; i < total; i++)
	{
		printf("%c", TILDA);
	}
}

int main()
{
	//the first box in the array is empty or 0 to make it easier
	//to calculate the months since array index starts with 0
	//and Janurary numeric notation is 1
	char *months[] = {" ", "Janurary", "Feburary", "March", "April", "May","June",
	"July", "August", "September", "October", "Novemeber", "Decemeber"};
	char *days[] = {" ", "Sun", "Mon", "Tue", "Wed", "Thu","Fri", "Sat"};
  int DaysOfMonth[] = {0, 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

	printf("Enter a year you wish to view the calendar for: ");
	int Year;
	scanf("%d", &Year);

	//For edge cases of user inputting negative numbers 
	while (Year < 0)
	{
		printf("Please enter a year that is not negatvie");
		scanf("%d", &Year);
	}

	printf("The year you enter is: %d\n", Year);

	if((Year % FOURHUNDRED == 0 && Year % 100 == 0) || Year % FOUR == 0)
	{
		printf("Yes it is a leap year.\n");
		DaysOfMonth[TWO] = DaysOfMonth[TWO] + 1;
	}else
	{
		printf("No it is not a leap year.\n")
	}

	int startDayOfWeek = calculateDayZero(Year);

	for(int month = 1; month < 12; month++)
	{
		int firsthalf, secondhalf;
		int length = strlen(months[month]);
		int total = MAX - length;
		int startingDay;

		//to make the calendar look even when displayed
		if(total % TWO != 0 )
		{
			firsthalf = (total / 2) + 1;
		}else
		{
			firsthalf = (total / 2);
		}
		secondhalf = total / 2;

		printf("\n\n");
		printTilda(firsthalf);
		printf("%s", months[month]);
		printTilda(secondhalf);
		printf("\n");

		//To make the spacing of numbers be under the days of the week
		for(int day = 1; day <=7; day++)
		{
			printf("%s       ", days[day]);
		}

		printf("\n");

		//print the the starting day based on the previous month
		for(startingDay = 0; startingDay < startDayOfWeek; startingDay++)
		{
			if(startingDay == 0)
			{
				printf("  ");
			}else
			{
			printf("          ");
		  }
		}

		for(int days = 1; days <= DaysOfMonth[month]; days++)
		{
			//to print out the days for Sunday
			if(startDayOfWeek == 0)
			{
				printf(" %d", days);
				startDayOfWeek++;
			}else
			{
			//for special case of when the number transfer from
			//single digit to double digit
			if(days == TEN)
			{
				printf("%11d", days);
			}else
			{
			printf("%10d", days);
		  }
			//to keep track which day of the week is it
			startDayOfWeek++;
			}
			//reset the counter to keep trakc which day of the week
			if(startDayOfWeek == DAYSOFWEEK)
			{
				printf("\n");
				startDayOfWeek = 0;
			}
			//set up the next month starting day of the week
			startingDay = startDayOfWeek;
		}
		printf("\n");
	}
	return 0;
}
