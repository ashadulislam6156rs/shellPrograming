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


