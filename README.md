#How To Wordle 

Use project gutenberg frequency sorted top 40000 words:
```
$ cat parser.py 
import sys; 
from bs4 import BeautifulSoup; 
s = BeautifulSoup(sys.stdin.read()); 
for x in s.find("div", class_="mw-parser-output").find_all("tr"): 
    print(x.find_all("td")[1].text)

curl https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/PG/2006/04/1-10000 | python3 parser.py > 1-10000.txt
curl https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/PG/2006/04/10001-20000 | python3 parser.py > 10001-20000.txt
curl https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/PG/2006/04/20001-30000 | python3 parser.py > 20001-30000.txt
curl https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/PG/2006/04/30001-40000 | python3 parser.py > 30001-40000.txt

cat 1-10000.txt 10001-20000.txt 20001-30000.txt 30001-40000.txt > 1-40000.txt

$ egrep -i '^[a-z][a-gi-z][a-hj-z][a-z]t$' 1-40000.txt  | grep -vi s | grep -vi r | head -n5
about
might
night
light
doubt
```
