# shellPrograming

#Palindrome

#!/bin/bash
echo "Enter a string or number:"
read str

# Reverse the string
rev=$(echo $str | rev)

if [ "$str" == "$rev" ]
then
  echo "$str is a Palindrome"
else
  echo "$str is NOT a Palindrome"
fi


#Leeep Year

#!/bin/bash
echo "Enter a year:"
read year

if [ $((year % 400)) -eq 0 ]
then
  echo "$year is a Leap Year"
elif [ $((year % 100)) -eq 0 ]
then
  echo "$year is NOT a Leap Year"
elif [ $((year % 4)) -eq 0 ]
then
  echo "$year is a Leap Year"
else
  echo "$year is NOT a Leap Year"
fi

#caumalabe Sum

#!/bin/bash
echo "Enter a number:"
read num

sum=0
i=1

while [ $i -le $num ]
do
  sum=$((sum + i))
  echo "After adding $i → Sum = $sum"
  i=$((i+1))
done

echo "Final Cumulative Sum = $sum"




#Algorithm Sjf

#include <iostream>
using namespace std;

struct Process {
    int pid;   // Process ID
    int at;    // Arrival Time
    int bt;    // Burst Time
    int wt;    // Waiting Time
    int tat;   // Turnaround Time
    bool done; // Process finished or not
};

int main() {
    int n;
    cout << "Enter the number of processes: ";
    cin >> n;

    Process p[n];

    // Input Arrival and Burst Times
    for (int i = 0; i < n; i++) {
        p[i].pid = i + 1;
        cout << "Enter Arrival Time for Process " << p[i].pid << ": ";
        cin >> p[i].at;
        cout << "Enter Burst Time for Process " << p[i].pid << ": ";
        cin >> p[i].bt;
        p[i].done = false;
    }

    int completed = 0, currentTime = 0;
    float totalWT = 0, totalTAT = 0;

    cout << "\nProcess execution order (Gantt Chart):\n|";

    while (completed < n) {
        int idx = -1;
        int minBT = 1e9;

        // Select process with shortest burst time among arrived processes
        for (int i = 0; i < n; i++) {
            if (!p[i].done && p[i].at <= currentTime && p[i].bt < minBT) {
                minBT = p[i].bt;
                idx = i;
            }
        }

        // যদি কোনো process ready না থাকে → সময় বাড়াও
        if (idx == -1) {
            currentTime++;
            continue;
        }

        // Waiting Time = CurrentTime - ArrivalTime
        p[idx].wt = currentTime - p[idx].at;
        // Turnaround Time = Waiting + Burst
        p[idx].tat = p[idx].wt + p[idx].bt;
        // Gantt Chart এ প্রিন্ট
        cout << " P" << p[idx].pid << " |";
        
        currentTime += p[idx].bt;
        p[idx].done = true;
        completed++;

        totalWT += p[idx].wt;
        totalTAT += p[idx].tat;
    }

    // Output Table
    cout << "\n\nProcess\tAT\tBT\tWT\tTAT\n";
    for (int i = 0; i < n; i++) {
        cout << "P" << p[i].pid << "\t" << p[i].at << "\t" << p[i].bt 
             << "\t" << p[i].wt << "\t" << p[i].tat << "\n";
    }

    cout << "\nAverage Waiting Time = " << totalWT / n;
    cout << "\nAverage Turnaround Time = " << totalTAT / n << endl;

    return 0;
}



