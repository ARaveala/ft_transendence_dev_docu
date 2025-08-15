## III.3 Game
The game must be a two-player, real-time Pong game. It needs to be playable on a single machine with a single keyboard,
but it also needs to have a system for user authentication and user profiles. The common display ratio is 16:9 aspect ratio.

The main purpose of this website is to play Pong versus other players.
-  Users must be able to participate in a live Pong game against another player directly
on the website. Both players will use the same keyboard. The Remote players
module can enhance this functionality with remote players.
-  A player must be able to play against another, and a tournament system should
also be available. This tournament will consist of multiple players who can take
turns playing against each other. You have flexibility in how you implement the
tournament, but it must clearly display who is playing against whom and the order
of the play.
-  A registration system is required: at the start of a tournament, each player must
input their alias. The aliases will be reset when a new tournament begins. However, this requirement can be modified using the Standard User Management
module.
-  There must be a matchmaking system: the tournament system should organize
the matchmaking of the participants, and announce the next match.
-  All players must adhere to the same rules, including having identical paddle speed.
This requirement also applies when using AI; the AI must exhibit the same speed
as a regular player.
-  The game must adhere to the default frontend constraints (as outlined above), or
you may choose to use the FrontEnd module, or override it with the Graphics
module. While the visual aesthetics can vary, the game must still capture the
essence of the original Pong (1972).

Modules that help fulfill the requirements
- Major module: Standard user management...: This module is a direct requirement for the game, as you need user profiles and authentication.
- Minor module: Game customization options: While not required, this module would allow for customization of the game (e.g., power-ups, different maps) which adds to the gameplay.
- Major module: Introduce an AI opponent: The base game is two-player. This module adds the option for a user to play against an AI when a second human player isn't available.
