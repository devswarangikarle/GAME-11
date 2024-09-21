# GAME-11

Given a list of N batsmen and M bowlers, each with a given cricketing skill, the selectors are asked to pick a team of 11 players such that the team has at least 4 batsmen and 4 bowlers.
Find is the maximum total cricketing skill of a team which they can form.
Note that the total cricketing skill is the sum of cricketing skills of all the players in the team.
Print -1 if making a valid team is not possible.

def max_team_skill(N, M, batsmen, bowlers):
    if N < 4 or M < 4:
        return -1
    
    batsmen.sort(reverse=True)
    bowlers.sort(reverse=True)
    
    selected_batsmen = batsmen[:4]  
    selected_bowlers = bowlers[:4]  
    
    remaining_players = batsmen[4:] + bowlers[4:]    
    remaining_players.sort(reverse=True)    
    selected_remaining = remaining_players[:3]    
    total_skill = sum(selected_batsmen) + sum(selected_bowlers) + sum(selected_remaining)
    
    return total_skill
import sys
input = sys.stdin.read
data = input().split()

t = int(data[0])
index = 1
results = []

for _ in range(t):
    N = int(data[index])
    M = int(data[index + 1])
    batsmen = list(map(int, data[index + 2: index + 2 + N]))
    bowlers = list(map(int, data[index + 2 + N: index + 2 + N + M]))
    index += 2 + N + M
    
    results.append(str(max_team_skill(N, M, batsmen, bowlers)))

sys.stdout.write("\n".join(results) + "\n")
