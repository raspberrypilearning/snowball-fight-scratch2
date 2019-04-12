## The target

Let's add in a target for your snowballs!

--- task ---

Add in another sprite to your project.

![a target sprite on the stage](images/snow-bear.png)

[[[generic-scratch-sprite-from-library]]]

--- /task ---

--- task ---

Add this code to your new sprite, so that it says "You got me!" when it gets hit:

![target sprite](images/target-sprite.png)

```blocks
when flag clicked
forever
	if < touching [snowball v]? > then
		say [You got me!] for (1) secs
	end
end
```

--- /task ---

--- task ---

Test out your new code.

![target sprite saying you got me!](images/snow-hit.png)

--- /task ---

--- task ---

task

--- /task ---

--- task ---

Let's do a couple of things to make the game harder. First, let's move the bear each time the player throws the snowball.

To do this, first add a `broadcast`{:class="blockcontrol"} to your snowball, near the top of your `forever`{:class="blockcontrol"} loop. This will let your bear know that a new shot is about to be taken.

![snowball sprite](images/snowball-sprite.png)

```blocks
when flag clicked
forever
set [power v] to (0)
+broadcast [new shot v]
wait (0.5) secs
go to x:(-200) y:(-130)
point in direction (90 v)
switch costume to [snowball-aim v]
show
repeat until <mouse down?>
	point towards [mouse-pointer v]
end
repeat until < not <mouse down?> >
	change [power v] by (1)
	wait (0.1) secs
end
broadcast [throw v] and wait
end
```

When your bear receives this message, move it to a new random position with this code:

![target sprite](images/target-sprite.png)

```blocks
when I receive [new shot v]
set x to (pick random (0) to (200))
```

--- /task ---

--- task ---

Test your project by throwing a few snowballs. Does your target move position each time?

--- /task ---

--- task ---

You can also make your game harder by adding a rock in front of your snowball.

![rock sprite on the stage](images/snow-rock.png)

--- /task ---

--- task ---

You can now change your snowball code, to stop when it touches the edge of the screen _or_ when it touches the rock. 

![snowball sprite](images/snowball-sprite.png)

```blocks
when I receive [throw v]
switch costume to [snowball v]
+ repeat until << touching [edge v]? > or <touching [Rocks v]?>>
	move (power) steps
	if <(power) > [0]> then
	change [power v] by (-0.25)
	end
end
hide
```

--- /task ---

--- task ---

Finally, you can make your game harder by making your snowball and your bear smaller.

![small snowball and target sprite](images/snow-small.png)

--- /task ---
