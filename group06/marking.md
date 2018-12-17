# Pacman Specification Marking 

## Marking

| Student Number | Design | Correctness | Unambiguous | Completeness | Consiseness | Overall |
|----------------|--------|-------------|-------------|--------------|-------------|---------|
| 18009415       | 0      | 7           | 7           | 9            | -0          | 23      |
| 18014801       | 0      | 6           | 6           | 7            | -0          | 19      |
| 18012035       | 0      | 8           | 7           | 7            | -0          | 22      |
| 18100537       | 0      | 7           | 6           | 7            | -0          | 20      |



## Individual Feedback

### 18009415

General : ERROR : "Type has decimal value 0011" , should be "binary value" ?

General : In lack of Sanity check fallback, what should we do when we receive an unexpected number of POSX for example?

Line 80 : Unclear "The remote computer can initialise any state" what state?

Line 106 : If `PACMAN_LEFT` is sent when returning home, then what's the point of `PACMAN_HOME`?

Line 150 : `PACMAN_HOME` is sent from REMOTE to LOCAL to forcibly return it. It is different from other messages.

Line 185, 188 : Why range 650, 800 ? Should specify beforehand.
> e.g. Specify the number : The game map is 650 * 800.

Line 350 : `EAT_UPDATE` shall also include whether it is a powerpill.

### 18014801

General : Hard to read with so many seperate sections. (No deduction for this)

General : No citation at all when directly copying stuff. (No deduction for this)

General : Unable to specify which bit is exactly the message. 
> e.g. MAZE: maze = ...  (is MAZE included in the message ?) should use "" to specify.

General : Message doesn't comply with descriptions.
> e.g. "EAT" must immediately follow a newline character. EAT:xposition ... (where is the \n?)

General : Extra redundant message.
> e.g. `GO_HOME` message is like `GOHOME:home=GO_HOME\n` Why?

General : In lack of Sanity check fallback, what should we do when we fail the sanity check?

General : This text encoding protocol is hard to implement with lots of extra string parsing. (No dedcution for this)

`MAZE` `PACMAN_UPDATE`: Didn't specify magic numbers like 31 and 84.

`GAME_STATUS` : In lack of `FRIGHTEN` and `CHASE` and `INIT` gamestatus.

`FOREIGN_PACMAN` : Ambigious Message Type. Better call it `FOREIGN_PACMAN_STATUS`.

`FOREIGN_PACMAN` : <foreign_pacman_arrived> Should specify encoding for bool value. <foreign_pacman_arrived> not understandable. 
> "It MUST be true when our pacman enters the REMOTE game object and false when our pacman exits the REMOTE game object and this value MUST be different from the Boolean which has the value of true if our pacman is AWAY and false for it is local"

`PACMAN_UPDATE` `GHOST_UPDATE`: ambigious descritpion for <speed>. Should talk about "decimla encoding of a float"? How?

`GHOST_UPDATE` : not understandable <ghostnum>
> :"<ghostnum>is a decimal encoding of an integer used to represent the number of the ghost our pacman just art."

### 18012035

General : should specify payload's total length / binary stream's total length, such that we can estimate the package size.
> e.g. rows and columns for `MAZE` message

General : should also specify what `MAZE (00)` beforehand. (No deduction for this)
> e.g. Say (00) is the Type field before saying `MAZE (00)`

Line 125 : `PACMAN_ZONE` message description is ambigious, "AWAY Pacman" is the same as "FOREIGN Pacman" if correctly understood, otherwise there is a faulty design.

Line 173 : Extra information that might not be necessary. FOREIGN Pacman doens't interact with `EYES` and `FRIGHTEN_TRAPPED` ghosts.

Line 244 : "Length of maze payload in bits?" Do we know what to expect? Is it width * length? or ?
should specifiy according to maze1.txt.

Line 256 : Do we have bit alignment for this message? (6 bit message ?)

Line 324 : Inconsistent Formatting POSITION and position. (No deduction for this)

Line 356 : Should specify which ghost Ghost Number represents. (No deduction for this)
> e.g. pink ghost -> ghost 1.

Line 360 : Didn't specify Score type. Is it an integer?

### 18100537

General : why `maze update` is not captialised? (No deduction for this)

General : Is this `Server - Client model` or `Peer to Peer model`? As said "no difference between ...", the model of the game should be `peer to peer model`.

General : Should draw diagram to better indicate the encoding of messages, (as well as illustrating byte alignment).

General : No byte alignment in messages.
> e.g. Message length : 28 bits (should be 8 * 4 = 32 bits)

`Maze display` : how is it possible to set game frame rate same on all computers? It is dependant on the performance capacity of each computer.

`5) GHOST UPDATE` : Didn't specifiy Message length

`5) GHOST UPDATE` : not understandable (Amongst other things, (like what?) thee mode ....)

`5) GHOST UPDATE` : may have unused message (No deduction for this)
> e.g. the ghost does not interact with pacman when in EYES or TRAPPED.
> SCATTER is also unnecessary as long as you have the position of ghosts
> Ghost is always moving, why do we have NONE direction?

`11) SCORE UPDATE` : Please specify Message type signifer: ... 

`12) STATUS UPDATE` : Please keep a universal formatting. Is `Message type signifier: 1100` same as `Message Type 1100` or is there a difference? Please specify.




