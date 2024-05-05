# Tunes-From-The-Past-Hackathon-Projesi
import pandas as pd
x = 0
print("Which sheet do you want? (Music or Podcast) (m/p)")
choice = input()
if choice == "m":
    x = 0

elif choice == "p":
    x = 1

else:
    print("Invalid input!")
    exit()
musicdata = pd.read_excel("[Excel filepath'i yaz]", sheet_name= x)
mset = pd.DataFrame(musicdata)
y = len(mset.index)
print(y)
print("Dataframe: \n\n", mset)

print("Select location:")
current_loc = input()
loc_choice = mset[mset["Location"] == current_loc]
print(loc_choice)
