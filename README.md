import time

def countdown(seconds, label):
  print(label)
  for x in range(seconds, 0, -1):
    secs = x % 60
    minutes = int(x // 60 ) % 60 
    print(f"{minutes:02}:{secs:02}", end="\r")
    time.sleep(1)
  print()

def Acycle(times, label):
  print(f"\nCycle {label - times + 1} of {label}")
  countdown(inhale_time, "inhale")
  countdown(hold_time, "hold tight")
  countdown(exhale, "exhale")


while True:
  preset = input("do you want the preset cycles?\n").strip().lower()
  if preset == "yes":
    break
  elif preset == "no":
    while True:
      try:
        inhale_time = int(input("how long do you want to inhale?\n").strip())
        if inhale_time > 0:
          break
      except ValueError:
        pass
    while True:
      try:
        hold_time = int(input("how long do you want to hold your breath?\n").strip())
        if hold_time > 0:
          break
      except ValueError:
        pass
    while True:
      try:
        option = (input("Do you want the default settings for exhale time or do you want to change it? Yes for change, No for the default settings.\n")).strip().lower()
        if option == "yes":
          while True:
            try:
              AB = int(input("how long do you want to exhale?\n").strip())
              if AB > 0:
                exhale = AB
                break
            except ValueError:
              continue
          break
        elif option == "no":
          exhale = inhale_time + 2 
          break  
      except ValueError:
        pass
    break


while True:
  if preset == "yes":
    preset1 = input("choose between calm, focus, and sleep.\n").strip().lower()
    if preset1 == "calm":
      inhale_time = 4
      hold_time = 4
      exhale = 6
      break
    elif preset1 == "focus":
      inhale_time = 5
      hold_time = 5
      exhale = 5
      break
    elif preset1 == "sleep":
      inhale_time = 4
      hold_time = 7
      exhale = 8
      break
    else:
      print("Please choose calm, focus, or sleep.")
  else:
    break

while True:
  try:
    cycle = int(input("how many times do you want the cycle to repeat\n").strip())
    if cycle > 0:
      break
    print("Please enter a positive number.")
  except ValueError:
    print("Please enter a valid number.")


for x in range(cycle, 0, -1):
  Acycle(x, cycle)
  time.sleep(1)

total_session = (inhale_time + hold_time + exhale) * (cycle)
seconds = total_session % 60
minutes = total_session // 60 
print(f"you have completed a {minutes:02}:{seconds:02} session in {cycle} cycles, well done :) ")# apnea-breath

