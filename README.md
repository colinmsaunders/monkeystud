MonkeyStud
==========

MonkeyStud is a poker variant, suitable for computer play.

The game is played with a 32 card deck, only the deuce through
nine are used. The best three card hand wins. The hand ranks are:
high card, pair, straight, flush, trips, straight flush.

Players are dealt four cards, the first face down, the rest face up.
There are betting rounds after the second, third, and fourth cards.

Up to eight players can play at once. Seats are shuffled before every hand. 
Each player starts with 1024 chips. Ante is 1/64th of total chips, divided 
evenly between all players, not more than any one player's stack.

A play is either fold, call, or bet. The bet amount is the size of
the pot, not more than any one player's stack.

A bot must implement the `play()` function. `play()` should return either
`'F'`, `'C'`, or `'B'` for Fold, Call, or Bet. Play takes three
arguments: `player_id`, `hand`, and `history`. `history` is a whitespace 
delimited list of player, action, value triples. Actions are:
Sit, Ante, face Down, face Up, Fold, Call, Bet, Reveal, and Win. 

A complete hand might look something like:

    a:S:1024
    b:S:1024
    a:A:16 
    b:A:16 
    a:D:xx 
    b:D:xx 
    a:U:2c 
    b:U:7d 
    a:C:0 
    b:B:32 
    a:F:0 
    b:W:64

Meaning, player A and player B sit with 1024 chips each, each antes 16 and 
is dealt a hole card face down, player A is dealt the deuce of clubs, B is 
dealt the seven of diamonds, player A checks, B bets 32, A folds, B wins 
64 chips.

To implement a bot, first get a copy of the game:

    $ git clone https://github.com/botfights/monkeystud.git
    $ cd monkeystud

To play against the computer:

    $ python monkeystud.py human

To play a game between computer and random:

    $ python monkeystud.py game p_computer p_random

Next, make a directory called `mybot` and copy over `p_computer/bot.py`,
edit the `play()` function, and play your bot against the computer:

    $ mkdir mybot
    $ cp p_computer/bot.py mybot/
    $ python monkeystud.py game mybot p_computer

To play a tournament of 100 games:

    $ python monkeystud.py tournament --num-games=100 mybot p_random p_computer

The winner of the tournament is the player who wins the most games,
in total. Note that `player_id` is consistent across games.

To verify your robot (to make sure it's not too slow, compared to `p_random`):

    $ python monkeystud.py verify mybot

Once your ready, upload your bot to http://botfights.io to challenge other
coders. See http://botfights.io/how-to-play for more information.

Have fun!

colinmsaunders@gmail.com
