# NFL Database
A SQLite database of NFL teams and games (dating back to 1970) and offensive player stats (dating back to 2009) taken by way of screen scraping the NFL.com website.

## Table Structure

###TEAM

| Column Name | Datatype | PK | FK | FK Table | Comments |
|---|---|---|---|---|---|
| TEAM_ID | Varchar | Yes | | | Team ID is the location-less team name (e.g. 'Ravens') |
| TEAM_ABBRV | Varchar | | | | 3 letter team abbreviation (e.g. 'BAL' for 'Baltimore Ravens') |
| CONFERENCE | Varchar | | | | 'NFC' or 'AFC' |
| DIVISION | Varchar | | | | 'North', 'South', 'East' or 'West' |
| LONG_NAME | Varchar | | | | Full team name (e.g. 'Baltimore Ravens') |

###GAME

| Column Name | Datatype | PK | FK | FK Table | Comments |
|---|---|---|---|---|---|
| GAME_ID | Numeric | Yes | | | |
| SEASON | Varchar | | | | Part of season ('PRE' for preseason, 'REG' for regular, and 'POST') |
| YEAR | Numeric | | | | Year of season (note: the nth season Pro Bowl and Super Bowl are played in the (n+1)th year |
| WEEK | Varchar | | | | Weeks range from 0 - 22 as a Varchar (was a mistake - see week_tmp)  |
| HOME_TEAM | Varchar | | FK | TEAM | |
| VISITING_TEAM | Varchar | | FK | TEAM | |
| HOME_TEAM_SCORE | Integer | | | | |
| VISITING_TEAM_SCORE | Integer | | | | |
| HOME_TEAM_RESULT | Varchar | | | | |
| VISITING_TEAM_RESULT | Varchar | | | | |
| GAME_DATE | Date | | |  | |
| DAY_OF_WEEK | Varchar | | | | 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday' |
| POST_SEASON_TYPE | Varchar | | | | 'Wild Card', 'Divisional Playoffs', 'Conference Championships', 'Super Bowl', 'Pro Bowl' |
| week_tmp | Integer | | | | Screwed up the WEEK column by not making it an Integer. Then screwed up the name for the new one. :/ |

###ROSTER

| Column Name | Datatype | PK | FK | FK Table | Comments |
|---|---|---|---|---|---|
| ROSTER_ID | Numeric | Yes | | | |
| TEAM_ID | Varchar | | FK | TEAM | |
| GAME_ID | Numeric | | FK | GAME | |

###PLAYER

| Column Name | Datatype | PK | FK | FK Table | Comments |
|---|---|---|---|---|---|
| PLAYER_ID | Numeric | Yes | | | Player ID taken from NFL.com |
| FIRST_NAME | Varchar | | | | |
| MIDDLE_NAME | Varchar | | | | |
| LAST_NAME | Varchar | | | | |
| NAME_SUFFIX | Varchar | | | | |
| HEIGHT | Numeric | | | | |
| WEIGHT | Numeric | | | | |
| BIRTH_DATE | Date | | | | |
| BIRTH_CITY | Varchar | | | | |
| BIRTH_STATE | Varchar | | | | |
| COLLEGE | Varchar | | | | |
| HIGH_SCHOOL | Varchar | | | | |
| HIGH_SCHOOL_CITY | Varchar | | | | |
| HIGH_SCHOOL_STATE | Varchar | | | | |

###PLAYER_STATS

| Column Name | Datatype | PK | FK | FK Table | Comments |
|---|---|---|---|---|---|
| PLAYER_STATS_ID | Numeric | Yes | | | |
| PLAYER_ID | Varchar | | FK | PLAYER | |
| ROSTER_ID | Numeric | | FK | ROSTER | |
| GAME_RESULT | Varchar | | | | 'W' or 'L' |
| GAME_PLAYED | Varchar | | | | '1' or '0' if they played in this game or not |
| GAME_STARTED | Varchar | | | | '1' or '0' if they started in this game or not  |
| PASS_COMPLETED | Integer | | | | Passes completed |
| PASS_ATTEMPTED | Integer | | | | Passes attempted |
| PASS_PERCENTAGE | Numeric | | | | Passing percentage |
| PASS_YARDS | Numeric | | | | Passing yards |
| PASS_AVERAGE_YARDS | Numeric | | | | Passing yards average |
| PASS_TD | Integer | | | | Passing touchdowns |
| PASS_INT | Integer | | | | Passing interceptions |
| PASS_SACK | Integer | | | | Sacks received as a QB |
| PASS_SACK_YARDS | Numeric | | | | Sacked yards as a passer |
| PASS_RATING | Numeric | | | | Passer Rating |
| RUSH_ATTEMPTS | Integer | | | | Rushing attmpts |
| RUSH_AVERAGE | Numeric | | | | Rushing yards average |
| RUSH_LONG | Numeric | | | | Rushing yards longest |
| RUSH_TD | Numeric | | | | Rushing touchdowns |
| FUMBLES | Numeric | | | | Fumbles |
| FUMBLES_LOST | Numeric | | | | Fumbles lost |
| RECEIVING_RECEPTIONS | Integer | | | | Receptions |
| RECEIVING_YARDS | Numeric | | | | Receiving yards |
| RECEIVING_AVERAGE | Numeric | | | | Receiving yards average |
| RECEIVING_LONG | Numeric | | | | Receiving yards longest |
| RECEIVING_TD | Integer | | | | Receiving touchdowns |
| FG_BLOCKED | Integer | | | | Field goals blocked |
| FG_LONG | Numeric | | | | Field goal - longest made |
| FG_ATTEMPTS | Integer | | | | Field goals attempted |
| FG_MADE | Integer | | | | Field goals made |
| FG_PERCENT | Numeric | | | | Field goal percentage |
| XP_BLOCKED | Integer | | | | Extra points blocked |
| XP_ATTEMPTS | Integer | | | | Extra points attempted |
| XP_MADE | Integer | | | | Extra points made |
| XP_PERCENT | Numeric | | | | Extra point percentage |
| KICKOFFS | Integer | | | | Kickoffs |
| KICKOFFS_AVERAGE | Numeric | | | | Kickoffs average |
| KICKOFFS_TOUCHBACKS | Numeric | | | | Kickoffs - touchbacks |
| KICKOFFS_RETURNED | Numeric | | | | Kickoffs - returned |
| KICKOFFS_AVERAGE | Numeric | | | | Kickoffs - returned |
| RECEIVING_LONG_TD | Varchar | | | | Receiving yards longest went for a touchdown ('1' or '0') |
| RUSH_LONG_TD | Varchar | | | | Rushing yards longest went for a touchdown ('1' or '0') |
