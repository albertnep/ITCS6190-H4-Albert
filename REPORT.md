# Hands-on L4 — Report

**Name:** Albert
**Student ID:** 801291837
**Email:** abastako@charlotte.edu

---

## What I ran

The commands you used, in the order you used them. If you deviated from the steps in the
README, say where and why.

```bash
docker compose up -d

mvn clean package

docker cp target/WordCountUsingHadoop-0.0.1-SNAPSHOT.jar resourcemanager:/tmp/

docker cp shared-folder/input/data/input.txt resourcemanager:/tmp/

docker exec -it resourcemanager bash
cd /tmp

hadoop fs -mkdir -p /input/data
hadoop fs -put ./input.txt /input/data
hadoop fs -ls /input/data

hadoop fs -cat /output/*

hdfs dfs -get /output /tmp/
exit

docker cp resourcemanager:/tmp/output/. shared-folder/output/

docker compose down

```

---

## Input and output

### My input dataset

```
I AM SAM. I AM SAM. SAM I AM.

THAT SAM-I-AM! THAT SAM-I-AM! I DO NOT LIKE THAT SAM-I-AM!

DO WOULD YOU LIKE GREEN EGGS AND HAM?

I DO NOT LIKE THEM,SAM-I-AM.
I DO NOT LIKE GREEN EGGS AND HAM.

WOULD YOU LIKE THEM HERE OR THERE?

I WOULD NOT LIKE THEM HERE OR THERE.
I WOULD NOT LIKE THEM ANYWHERE.
I DO NOT LIKE GREEN EGGS AND HAM.
I DO NOT LIKE THEM, SAM-I-AM.

WOULD YOU LIKE THEM IN A HOUSE?
WOULD YOU LIKE THEN WITH A MOUSE?

I DO NOT LIKE THEM IN A HOUSE.
I DO NOT LIKE THEM WITH A MOUSE.
I DO NOT LIKE THEM HERE OR THERE.
I DO NOT LIKE THEM ANYWHERE.
I DO NOT LIKE GREEN EGGS AND HAM.
I DO NOT LIKE THEM, SAM-I-AM.

WOULD YOU EAT THEM IN A BOX?
WOULD YOU EAT THEM WITH A FOX?

NOT IN A BOX. NOT WITH A FOX.
NOT IN A HOUSE. NOT WITH A MOUSE.
I WOULD NOT EAT THEM HERE OR THERE.
I WOULD NOT EAT THEM ANYWHERE.
I WOULD NOT EAT GREEN EGGS AND HAM.
I DO NOT LIKE THEM, SAM-I-AM.

WOULD YOU? COULD YOU? IN A CAR?
EAT THEM! EAT THEM! HERE THEY ARE.

I WOULD NOT, COULD NOT, IN A CAR.

YOU MAY LIKE THEM. YOU WILL SEE.
YOU MAY LIKE THEM IN A TREE!

I WOULD NOT, COULD NOT IN A TREE.
NOT IN A CAR! YOU LET ME BE.
I DO NOT LIKE THEM IN A BOX.
I DO NOT LIKE THEM WITH A FOX.
I DO NOT LIKE THEM IN A HOUSE.
I DO NOT LIKE THEM WITH A MOUSE.
I DO NOT LIKE THEM HERE OR THERE.
I DO NOT LIKE THEM ANYWHERE.
I DO NOT LIKE GREEN EGGS AND HAM.
I DO NOT LIKE THEM, SAM-I-AM.

A TRAIN! A TRAIN! A TRAIN! A TRAIN!
COULD YOU, WOULD YOU ON A TRAIN?

NOT ON TRAIN! NOT IN A TREE!
NOT IN A CAR! SAM! LET ME BE!
I WOULD NOT, COULD NOT, IN A BOX.
I WOULD NOT, COULD NOT, WITH A FOX.
I WILL NOT EAT THEM IN A HOUSE.
I WILL NOT EAT THEM HERE OR THERE.
I WILL NOT EAT THEM ANYWHERE.
I DO NOT EAT GREEM EGGS AND HAM.
I DO NOT LIKE THEM, SAM-I-AM.

SAY! IN THE DARK? HERE IN THE DARK!
WOULD YOU, COULD YOU, IN THE DARK?

I WOULD NOT, COULD NOT, IN THE DARK.

WOULD YOU COULD YOU IN THE RAIN?

I WOULD NOT, COULD NOT IN THE RAIN.
NOT IN THE DARK. NOT ON A TRAIN.
NOT IN A CAR. NOT IN A TREE.
I DO NOT LIKE THEM, SAM, YOU SEE.
NOT IN A HOUSE. NOT IN A BOX.
NOT WITH A MOUSE. NOT WITH A FOX.
I WILL NOT EAT THEM HERE OR THERE.
I DO NOT LIKE THEM ANYWHERE!

YOU DO NOT LIKE GREEN EGGS AND HAM?

I DO NOT LIKE THEM, SAM-I-AM.

COULD YOU, WOULD YOU, WITH A GOAT?

I WOULD NOT, COULD NOT WITH A GOAT!

WOULD YOU, COULD YOU, ON A BOAT?

I COULD NOT, WOULD NOT, ON A BOAT.
I WILL NOT, WILL NOT, WITH A GOAT.
I WILL NOT EAT THEM IN THE RAIN.
NOT IN THE DARK! NOT IN A TREE!
NOT IN A CAR! YOU LET ME BE!
I DO NOT LIKE THEM IN A BOX.
I DO NOT LIKE THEM WITH A FOX.
I WILL NOT EAT THEM IN A HOUSE.
I DO NOT LIKE THEM WITH A MOUSE.
I DO NOT LIKE THEM HERE OR THERE.
I DO NOT LIKE THEM ANYWHERE!
I DO NOT LIKE GREEN EGGS AND HAM!
I DO NOT LIKE THEM, SAM-I-AM.

YOU DO NOT LIKE THEM. SO YOU SAY.
TRY THEM! TRY THEM! AND YOU MAY.
TRY THEM AND YOU MAY, I SAY.

sAM! IF YOU LET ME BE,
I WILL TRY THEM. YOU WILL SEE.

(... and he tries them ...)

SAY! I LIKE GREEN EGGS AND HAM!
I DO! I LIKE THEM, SAM-I-AM!
AND I WOULD EAT THEM IN A BOAT.
AND I WOULD EAT THEM WITH A GOAT...
AND I WILL EAT THEM, IN THE RAIN.
AND IN THE DARK. AND ON A TRAIN.
AND IN A CAR. AND IN A TREE.
THEY ARE SO GOOD, SO GOOD, YOU SEE!
SO I WILL EAT THEM IN A BOX.
AND I WILL EAT THEM WITH A FOX.
AND I WILL EAT THEM IN A HOUSE.
AND I WILL EAT THEM WITH A MOUSE.
AND I WILL EAT THEM HERE AND THERE.
SAY! I WILL EAT THEM ANYWHERE!
I DO SO LIKE GREEN EGGS AND HAM!
THANK YOU! THANK YOU, SAM I AM.
```

### The output the job produced

Paste the contents of your output file here.

```
NOT	67
LIKE	44
THEM	40
WOULD	27
AND	25
EAT	23
YOU	23
WILL	18
WITH	18
NOT,	15
COULD	14
EGGS	11
THE	11
HERE	11
GREEN	10
THEM,	10
YOU,	8
THERE.	8
HOUSE.	7
SAM-I-AM.	7
HAM.	6
MOUSE.	6
BOX.	6
FOX.	6
TRAIN!	5
ANYWHERE.	5
SAM-I-AM!	4
THEM!	4
LET	4
TRY	4
HAM!	3
SAY!	3
DARK.	3
TREE.	3
TREE!	3
THAT	3
CAR!	3
THEM.	3
CAR.	3
SEE.	3
RAIN.	3
ANYWHERE!	3
YOU?	2
DARK!	2
BE!	2
THEY	2
SAM	2
THANK	2
MAY	2
DARK?	2
TRAIN.	2
AM.	2
HAM?	2
SAM.	2
GOOD,	2
SAY.	2
BOAT.	2
ARE	1
GOAT...	1
RAIN?	1
CAR?	1
BE,	1
BE.	1
THEN	1
YOU!	1
and	1
MAY.	1
MAY,	1
GREEM	1
HOUSE?	1
GOAT!	1
TRAIN?	1
GOAT.	1
DO!	1
ARE.	1
MOUSE?	1
BOX?	1
them	1
FOX?	1
...)	1
sAM!	1
GOAT?	1
BOAT?	1
(...	1
THEM,SAM-I-AM.	1
THERE?	1
tries	1
SAM!	1
SAM,	1
SEE!	1
```

---

## What I observed


- Something I noticed was the first time running `mvn clean package` it took a while since it was downloading a bunch of dependencies but it was faster to run my second time.

- The map phase took about 1.9 seconds while the reduce phase took about 2.8 seconds so the mapping was faster.

- The output was ordered by decresing word frequeancy and did not take alphebetical order into consideration when two words have the same frequency. But I am sure this is something we could update in the code.

- the program treated words with different puncutation as different words. For example `NOT` and `NOT,` were treated as two different words.


---

## Problems and fixes

Error:
```
[ERROR] dependency: jdk.tools:jdk.tools:jar:1.8 (system)
[ERROR]         Could not find artifact jdk.tools:jdk.tools:jar:1.8 at specified path C:\Program Files (x86)\Java\jre-1.8/../lib/tools.jar
[ERROR] 
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/DependencyResolutionException
```
This error stemed from me having a java JRE and not a JDK installed originally. Hadoop and requires a tool found in JDK so to solve this I installed java JDK and rerouted my system variables to the new JDK

