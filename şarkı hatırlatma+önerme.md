# Tunes-From-The-Past-Hackathon-Projesi
import pandas as pd
import time

#Kullanıcının dinlediği şarkıların listesi
musicdata = pd.read_excel("Music_list.xlsx filepath") #filepathi kullanıcı kendisi eklemeli
mset = pd.DataFrame(musicdata)
print("Songs you have listened to: \n\n", mset)
print("Select location:")
#Bu normalde telefonun GPS'inden alınıcak
current_loc = input()
loc_choice = mset[mset["Location"] == current_loc]
print("Songs you have listened to at", current_loc, "are:")
time.sleep(1)
if len(loc_choice) == 0:
    print("Nothing!")
    time.sleep(1)
    print("Listen to some songs at", current_loc,  "in order for reminders and location based suggestions to appear!")
    time.sleep(1)
    exit()
else:
    print(loc_choice)
time.sleep(2)

genre_values = loc_choice['Genre'].values
most_common_genre = pd.Series(genre_values).mode()[0]
#Fizy platformundaki tüm müziklerin listesi (Gerçek değil, prototip için hazırlanmıştır)
systemdata = pd.read_excel("system_database.xlsx filepath")
sset = pd.DataFrame(systemdata)
gen_choice = sset[sset["Genre"] == most_common_genre]
print("Here are our recommendations by looking at what you played at", current_loc, ":")
time.sleep(2)
print(gen_choice)
time.sleep(2)
