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
The tournament manager will enter the entry price.
The tournament manager will enter all player usernames. For simplicity, let’s assume that there will be either 8 or 16 players in a tournament.
When the tournament manager has entered the above information, the system will display, in addition to the player names, the potential prizes and profit, as calculated in the TourneyCalc app that you developed for Assignment 4. The tournament manager will then be able to double check the information and start the tournament.
