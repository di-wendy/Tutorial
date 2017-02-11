#Requirements

###1. The tournament is organized as a single elimination tournament with third place playoff.

Not considered because it does not affect the design directly.

###2. The application has two modes: tournament manager and tournament player. You can assume that the mode is selected when the application starts, with no authentication involved.
To realize this requirement, I added to the design classes "player" and "manager".

###3.The tournament manager uses the system to (1) add players, (2) run tournaments, and (3) display prizes and profits.
I added relationship "Add" between player and manager, "Create" between manager and tournament. Also, I added a class called manger_display to handle the display of prizes and profits.

###4.The tournament players use the system to (1) view the match list and (2) view the total player prizes.
I added a class "player_display". The "player" class has the attribute “total” to represent the total player prizes.

###5.The app has an underlying database to save persistent information across runs (e.g., players in the system, status of ongoing tournaments).
This requirement can be realized through realizing other requirements.

###6.A player in the system is characterized by the following information:(1) Name (2) Unique alphanumeric username (3) Numeric phone number (4) A deck choice, from a list of deck options
The player class has the following attributes -- “Name”, “Username”, “Phone”, “Deck_Choice”.

###7.The tournament manager can add a player to and remove a player from the system.
I added relationship “add” and “remove” between the player and manager.

###8.There can only be one ongoing tournament at any given time.
There is a boolean attribute in “Tournament” class. If the current tournament is ongoing, no new tournament can be created.

###9.To start a tournament: The tournament manager will enter the house cut.
###(1) The tournament manager will enter the entry price.
###(2) The tournament manager will enter all player usernames. For simplicity, let’s assume that there will be either 8 or 16 players in a tournament.
###(3) When the tournament manager has entered the above information, the system will display, in addition to the player names, the potential prizes and profit, as calculated in the TourneyCalc app that you developed for Assignment 
###(4) The tournament manager will then be able to double check the information and start the tournament.
I added relationship “Creat” between manager and tournament.The "tournament" class has attribute as "Time_stamp",generate through the system ultility function. It also has attributes -- "House_cut", "Entry_Price" input by manager when creating the "tournament". The inital ongoing status is set to "True" .While ended by the manager, the status will be set to "False".

###10.When there is no ongoing tournament, the player mode will show totals for every player in the system as a list sorted by total.
Class Player_No_Ongoing_Display is created. The player's attribute "total" will be updated after each tournament, hence a query can be easily done to generate the "Player_No_Ongoing_Display".

###11.When a tournament is ongoing, the player mode will show a match list. The match list displays a list of players paired with other players representing ongoing matches, matches ready to be played, and results from completed matches.
There is an underlying database for "Match"s, and the "Match" has the "status" and "result", therefore the class "Player_Ongoing_Display" can easily be generated.

###12. When a tournament is ongoing, the manager mode will also show a match list. In this case, however, the tournament manager will be able to:
###(1)Start a match ready to be played by selecting it from the list. The system will then mark the game between the specified players as started.
Manager has the operation “Start” to the Match. The match has attribute as “Status”, which can be marked as “started” when started.

###(2)End an ongoing match and specify a result for it.
Manager has the operation “End” to the Match. The match has attribute as “Status”, which can be marked as “completed”, the result attribute can also be marked.

###(3)End the tournament. If the tournament is ended early, money is refunded.
Manager has the operation “End” to the Match. The refunded money will not affect our design.

###13. After a tournament is completed, prizes for the winning player, the second place player, and the third place player (who wins the third place playoff) will be recorded in the underlying database. 
I added operation “update_total” between tournament and players. When tournaments ends, the method will be called to update the total based on first/second/third Prize. There will also be a class "Winer_List" which recorded the winners' username through "1st", "2nd" ,"3rd" be generated when the tournament ends.

###14. After a tournament is completed, the house profit will also be recorded in the underlying database.
Created a class called “House_profit” with attributes as “Profit”. When the tournament is completed, it will generate a house_profit. The profit depends on the tournament’s attributes and the time_stamp is inherited from the "Tournament".

###15. When there is no ongoing tournament, the tournament manager can:
###View totals for every player in the system as a list sorted by total. From there, the manager can also view a list of the player’s individual prizes by selecting the player from the list.
The "Manager_No_Ongoing_Display" can display the players by total. It can also display the player's prize from querying the stored "Winner_List".
###View the list of past house profits in chronological order and the total.
The "Manager_No_Ongoing_Display" can display the players' past house profit from "House_profit" stored in underlying database. Timestamps were inherited and total can be calculated.

###16. The User Interface (UI) must be intuitive and responsive.
Not considered because it does not affect the design directly.

