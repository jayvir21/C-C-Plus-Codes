diff -This line will appear red(like a deletion) - This line will appear in green(like an addition) + 
#include <stdio.h>
void printCalendar(int year, int month) {
<pre><code>```diff+ This line will showup in green on Github- This line should be red! This might be orange```</code></pre>
 {
    int daysInMonth, startDay;
   } 
    // Array storing number of days in each month (excluding leap years)
    int days[] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

    // Adjust for leap years
    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0))
        days[1] = 29;

    // Calculate the start day of the month using Zeller's Congruence formula
    int q = 1; // First day of the month
    int m = (month < 3) ? (month + 12) : month;
    int y = (month < 3) ? (year - 1) : year;
    int h = (q + ((13 * (m + 1)) / 5) + y + (y / 4) - (y / 100) + (y / 400)) % 7;
    startDay = (h + 6) % 7; // Adjusting for Sunday-based week

    daysInMonth = days[month - 1];

    // Print the calendar
    printf("\n   Calendar - %d/%d\n", month, year);
    printf(" Su Mo Tu We Th Fr Sa\n");

    // Print leading spaces
    for (int i = 0; i < startDay; i++)
        printf("   ");

    // Print dates
    for (int day = 1; day <= daysInMonth; day++) {
        printf("%3d", day);
        if ((day + startDay) % 7 == 0)
            printf("\n");
    }
    printf("\n");
}

int main() {
    int year, month;
    printf("Enter year and month (e.g., 2025 5): ");
    scanf("%d %d", &year, &month);

    if (month < 1 || month > 12) {
        printf("Invalid month! Please enter a value between 1 and 12.\n");
        return 1;
    }

    printCalendar(year, month);
    return 0;
}
