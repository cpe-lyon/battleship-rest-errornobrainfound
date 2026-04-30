# Conception  

## Liste endpoints  

BASE_URL => http(s)://<ip/domaine>/api  

**Fomat JSON** en sortie  

*Protected* => signifie qu'il faut être authentifié  

**JWT** contient id du joueur et username (ou displayname)  

## Authentification  

- /users (POST)  
params : username, email, password  
return : http_code  

- /auth/login (POST)  
params: email, password  
return : http_code +/ jwt  

- /auth/logout (POST) *Protected*  
params : ?  
return : http_code  

- /auth/password/forgot (POST)  
params : email  
return : http_code  

- /auth/password (PUT) *Protected*  
params : current_password, new_password  
return : http_code  

- /users/{user_id} (GET) *Protected*  
params : ?  
return : http_code + user  

- /users/{user_id} (PUT/PATCH) *Protected*  
params : valeur(s) modifiée(s)  
return : http_code  

- /users/{user_id} (DELETE) *Protected*  
params : ?  
return : http_code  

- /users (GET) *Protected*  
params : pagination, filtres éventuels  
return : http_code + users[]  

## Lobby *Protected*  

- /games/{game_id}/players/{player_id}/ready (PUT)  
params : ready (bool)  
return : http_code  

- /games/{game_id} (PATCH)  
params : nbr_joueurs, teams, taille_grille, ...  
return : http_code  

- /games/{game_id}/players/{player_id} (DELETE)  
params : ?  
return : http_code  

- /games/{game_id}/spectators (POST)  
params : ?  
return : http_code  

## Déroulé partie *Protected*  

- /games (GET)  
params : ?
return : http_code + liste parties en attente

- /games/boats (GET)  
params : ?  
return : http_code + liste Objets boats  

- /games (POST)  
params : nbr_joueurs, teams, ...  
return : http_code + game_id  

- /games/{game_id}/join (POST)  
params : team, slot éventuel  
return : http_code  

- /games/{game_id}/start (POST)  
params : ?  
return : http_code + initial game state  

- /games/{game_id}/players/{player_id}/boats (POST)  
params : tableau associatif avec id => (x,y)  
return : http_code  

- /games/{game_id}/shots (POST)  
params : (x,y)  
return : http_code + hit/miss  

- /games/{game_id}/shots (GET)  
params : pagination éventuelle  
return : http_code + shots[]  

- /games/{game_id}/players/me/board (GET)  
params : ?  
return : http_code + board (bateaux + tirs reçus)  

- /games/{game_id}/players/{player_id}/board (GET)  
params : ?  
return : http_code + board (vue masquée: hits/miss)  

- /games/{game_id}/forfeit (POST)  
params : ?  
return : http_code  

- /games/{game_id} (GET)  
params : ?  
return : http_code + game state  

- /games/{game_id}/players/{user_id} (DELETE)  
params : ?  
return : http_code  

## Statistiques *Protected*  

- /stats/{user_id} (GET)  
params : ?  
return : http_code + values  

- /stats/users/{user_id} (GET)  
params : ?  
return : http_code + values  
