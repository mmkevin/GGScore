GGScore
============

GGScore allows you to create easy to use leaderboards for your Corona SDK powered games.

Basic Usage
-------------------------

##### Require The Code
```lua
local GGScore = require( "GGScore" )
```

##### Create or load a scoreboard
```lua
local board = GGScore:new( "all" )
```

##### Set some values
```lua
box:set( "message", "hello, world" )
box.anotherValue = 10
```

##### Set the default name
```lua
board:setDefaultName( "Dave" )
```

##### Set the default score
```lua
board:setDefaultScore( 0 )
```

##### Set the maximum length allowed for player names
```lua
board:setMaxNameLength( 10 )
```

##### Set the maximum length allowed for scores
```lua
board:setMaxScoreLength( 3 )
```

##### Add a score with a name
```lua
board:add( "Bob", 25 )
```

##### Add a score with the default name
```lua
board:add( nil, 12 )
```

##### Add a name with the default score
```lua
board:add( "Jim", nil )
```

##### Display the scores in the console
```lua
board:print()
```

##### Retrieve the scores so that you can display them in your game
```lua
local scores = board:getScores()
```

##### Get all scores by 'Bob'
```lua
local scores = board:getScoresByPerson( "Bob" )
```

##### Save the leaderboard out to disk
```lua
board:save()
```

##### Load the pre-created leaderboard from disk
```lua
board:load()
```

##### Load and create a leaderboard from disk
```lua
local board = GGScore:load( "all" )
```

##### Destroy this GGScore object
```lua
board:destroy()
```

Update History
-------------------------

##### 0.1
Initial release