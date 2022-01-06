# Bar_-_Barh_with_Counter_in_Pandas_-_with_DictReader

import csv
from collections import Counter

with open('data.csv') as csv_file:
    csv_reader = csv.DictReader(csv_file)
    lang_counter = Counter()
    
    for row in csv_reader:
        lang_counter.update(row['LanguagesWorkedWith'].split(';'))
lang_counter.most_common(15)

language = []
popularity = []

for item in lang_counter.most_common(15):
    language.append(item[0])
    popularity.append(item[1])

language.reverse()
popularity.reverse()

plt.barh(language,popularity,color='b')
plt.title('Most Popular Languages')

plt.xlabel('Number of People who use')
plt.show()




import pandas as pd

data = pd.read_csv('data.csv')

ids = data['Responder_id']
lang_response = data['LanguagesWorkedWith']

language_counter = Counter()

for item in lang_response:
    lang_counter.update(item.split(';'))
    
print(lang_counter)
