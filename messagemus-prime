#!/bin/bash

gold=$(tput setaf 3)
magenta=$(tput setaf 5)
cyan=$(tput setaf 6)
default=$(tput sgr0)

function message_box() {
  # store the current cursor location
  tput sc

  # clear the top section for the message box
  clear_space

  # move the cursor to the upper left corner
  tput cup 0 0
    
  cols=`tput cols`
  TNUM=$(($cols - ${#1} - 4))
  MNUM=$((${#2} + ${#3} + 6))
  NUM=$((${#3} + 6))

  echo "${cyan}"

  # print the top of the info box
  echo -n "##${magenta} $1 ${cyan}"
  eval printf %.0s# '{1..'"${TNUM}"\}; echo

  # print the middle of the info box
  echo -n "#  ${gold}$2: ${default}$3${cyan}"

  # print the right of the info box
  tput cup 2 $cols
  echo -n "#"

  # print the bottom of the info box
  tput cup 3 0
  eval printf %.0s# '{1..'"${cols}"\}; echo

  echo "${default}"

  # return the cursor to its original position
  tput rc
}

# clear the first 4 lines of the terminal
function clear_space() {
  cols=`tput cols`
  for row in {0..3}
  do
    tput cup $row 0
    tput ech $cols
  done
}

# initialize the data array as an empty set
data=()

if [ -t 0 ];then
  # handle arguments passed in as non piped arguments
  message_box "$1" "$2" "$3"
else
  # handle arguments passed in from a pipe
  while read -r pipe;do

    #assemble the data array
    data=("${data[@]}" "$pipe")
    
    # if all message components are present
    if [ ${#data[@]} -ge 3 ];then
      
      # build the message box
      message_box "${data[0]}" "${data[1]}" "${data[2]}"

      # lets clear data so we can begin a new count
      data=()
    fi
  done
fi