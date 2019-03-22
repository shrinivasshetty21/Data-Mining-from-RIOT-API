## Gathering data from LoL games using RIOT API

The script in this repository is used for getting match statistics for League of Legends games using RIOT api from the North America region for the latest season.

### Dependencies 
Project is run using -
- Windows 10 
- Python 3.6.5.

### Installation
A requirements.txt is added to the repository which can be used to install the dependencies using the following code in your virtual environment.
```
pip install -r requirements.txt
```
### Inside the Repository
 - requirements.txt : Contains required packages list for running the script. 
 - data_gathering_riot.py : Script to get data using RIOT api.
 - League Of Legends Data Flow Chart.pdf : Flow chart for data gathering process using RIOT API.

#### Output Files
Output files by the program are as follows :
- lol_match_data.json : Match data in JSON format with match id as keys and match data as values.
``` 
lol_match_data_na1['2880125867'] : 
{'gameCreation': 1538672222234,
 'gameDuration': 1219,
 'gameId': 2880125867,
 'gameMode': 'ARAM',
 'gameType': 'MATCHED_GAME',
 'gameVersion': '8.19.246.5109',
 'mapId': 12, ...,
}
```
- Game_Stats_na1.json : Contains project related match data.
```
Game_Stats_na1[0] :
[76, 'GOLD', 32, 4, 'NONE', 'DUO_SUPPORT', 12, 450, 'ARAM', 2897852972, 1]
```
- Unused_Account_ID_na1.json : Contains list of account ids used to gather match data.
```
Unused_Account_ID_na1[0:5] :
[40937919, 230719307, 213603713, 39503890, 31649572]
```
- Used_Account_ID_na1.json : Contains list of account ids that have already been used to gather data.
```
Used_Account_ID_na1[0:5] : 
[31649572, 230988665, 214000277, 228376462, 42794183]
```
 - Match_ID_na1.json : Contains list of all the match ids already used to gather statistics. 
```
Match_ID_na1[0:5] : 
['2902063615', '2902035349', '2901918769', '2901743529', '2900738002']
```
### Testing Script
Before running the script make sure you have updated the code with an active API key provided by RIOT on their [developers pages](https://developer.riotgames.com/).
Update the following lines in the code.
```
# API key and loading file name.
KEY = 'YOUR API KEY'
```
Once the machine is ready with all the packages required and the script is updated with a new api key, run the script using the following command. The file requires a region index for choosing the region to gather LoL game statistics from.

##### Region keys are as follows:
###### North America = 0
###### Brazil = 1
###### Europe and Nordic Region = 2
###### Europe West = 3
###### Japan = 4
###### Latin America South = 5
###### Latin Americal North = 6
###### Oceanic = 7
###### Russia = 8
###### Turkey = 9
###### Korea = 10

The following command will gather data from the North America region.
```
$ cd project_directory/
$ python data_gathering_riot.py 0
```

### Additional Notes
Currently the script is programmed to store data after getting match information from 1000 accounts. As soon as the json file containing the match data becomes 2 gb in size the program will store the file with a different name and use an empty json file to store the new data.
