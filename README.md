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

##### Create or load a scoreboard and flag it so duplicate names are allowed
```lua
local board = GGScore:new( "best", true )
```

##### Create or load a scoreboard and attach it to a GameCenter leaderboard
```lua
local board = GGScore:new( "best", nil, "com.corona.best" )
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

##### Add a score and submit it to GameCenter ( you will need to already have GameCenter set up properly )
```lua
board:add( "Jim", 25, nil, true )
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

##### Display the scores in a basic list
```lua
local widget = require( "widget" )

local scores = board:getScores()

local listOptions = 
{
	top = 0,
	height = 480
}

local list = widget.newTableView( listOptions )

-- onRender listener for the tableView
local function onRowRender( event )
	
	local row = event.target
	local rowGroup = event.view

	local number = display.newRetinaText( "#" .. event.index .. " - ", 12, 0, "Helvetica-Bold", 18 )
	number:setReferencePoint( display.CenterLeftReferencePoint )
	number.x = 15
	number.y = row.height * 0.5
	number:setTextColor( 0, 0, 0 )
	
	local name = display.newRetinaText( scores[ event.index ].name, 12, 0, "Helvetica-Bold", 18 )
	name:setReferencePoint( display.CenterLeftReferencePoint )
	name.x = number.x + number.contentWidth
	name.y = row.height * 0.5
	name:setTextColor( 0, 0, 0 )
	
	local score = display.newRetinaText( scores[ event.index ].value, 12, 0, "Helvetica-Bold", 18 )
	score:setReferencePoint( display.CenterLeftReferencePoint )
	score.x = display.contentWidth - score.contentWidth - 20
	score.y = row.height * 0.5
	score:setTextColor( 0, 0, 0 )
	
	rowGroup:insert( number )
	rowGroup:insert( name )
	rowGroup:insert( score )
	
end

for i = 1, #scores, 1 do
	list:insertRow
	{
		onRender = onRowRender,
		height = 40
	}
end
```

##### Destroy this GGScore object
```lua
board:destroy()
```

Update History
-------------------------

##### 0.1
Initial release