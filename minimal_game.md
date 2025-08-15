## III.3 Game
The game must be a two-player, real-time Pong game. It needs to be playable on a single machine with a single keyboard,
but it also needs to have a system for user authentication  and user profiles. The common display ratio is 16:9.

The main purpose of this website is to play Pong versus other players.
-  Users must be able to participate in a live Pong game against another player directly
on the website. Both players will use the same keyboard. The Remote players [link remote players module]
module can enhance this functionality with remote players.
-  A player must be able to play against another, and a tournament system should
also be available. This tournament will consist of multiple players who can take
turns playing against each other. You have flexibility in how you implement the
tournament, but it must clearly display who is playing against whom and the order
of the play. <details/>
                <summary/> Tournament Implementation Concepts</summary>

              - Bracket System (Single or Double Elimination) Players are placed in a visual bracket. Winners advance, losers are eliminated     (or move to a lower bracket in double elimination). → Ideal for competitive formats with clear progression.
              - Round-Robin Format Every player plays against every other player once. → Great for small groups and fairness; ensures all players get equal playtime.
              - Swiss System Players are matched based on their win/loss record, without elimination. → Balances fairness and competitiveness; useful for larger tournaments.
              - Queue-Based Matchmaking Players are placed in a queue and matched sequentially. → Simple to implement; works well for casual or rolling-entry tournaments.
              - Manual Match Assignment Admin or host manually selects matchups and order. → Useful for custom events or when integrating with external systems.
              - Time-Slot Scheduling Matches are assigned specific time slots, and players are notified in advance. → Adds structure and predictability, especially for remote play.
              - Dynamic Matchmaking Based on Performance Matchups are generated dynamically based on player performance or ranking. → Adds a layer of strategy and progression.
              - Visual Timeline or Match Ladder Matches are displayed on a timeline or ladder view, showing progression and upcoming games. → Enhances clarity and user experience.
              </details>
-  A registration system is required: at the start of a tournament, each player must
input their alias. The aliases will be reset when a new tournament begins. However, this requirement can be modified using the Standard User Management module. [link standard user module]
-  There must be a matchmaking system: the tournament system should organize
the matchmaking of the participants, and announce the next match. (see drop down tournament implementation concepts)
-  All players must adhere to the same rules, including having identical paddle speed.
This requirement also applies when using AI; the AI must exhibit the same speed
as a regular player. (similar to irc, clients all utalize the same base code , ai would be the same same base code) [link ai module]
-  The game must adhere to the default frontend constraints (typescript as base), or
you may choose to use the FrontEnd module[link to front end module], or override it with the Graphics
module [link to graphics module]. While the visual aesthetics can vary, the game must still capture the
essence of the original Pong (1972).

Modules that help fulfill the requirements
- Major module: Standard user management...: This module is a direct requirement for the game, as you need user profiles and authentication.
- Minor module: Game customization options: While not required, this module would allow for customization of the game (e.g., power-ups, different maps) which adds to the gameplay.
- Major module: Introduce an AI opponent: The base game is two-player. This module adds the option for a user to play against an AI when a second human player isn't available.
