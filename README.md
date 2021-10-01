# PokemonTopTrumps
TopTrumps game using Pokemon API
import requests
import random



def random_pokemon():
  pokemon_number = random.randint(1, 151)
  url = 'https://pokeapi.co/api/v2/pokemon/{}/'.format(pokemon_number)
#pokemon_id = input('Enter the pokemon id: ')
#url = 'https://pokeapi.co/api/v2/pokemon/{}/'.format(pokemon_id)
  response = requests.get(url)
  random_pokemon = response.json()

  return { 
      'height': random_pokemon['height'],
      'weight': random_pokemon['weight'],
      'name': random_pokemon ['name'],
      'id': random_pokemon ['id']
      }

my_pokemon = random_pokemon()

def run():


  print('Your Pokemon is {}'.format(my_pokemon['name']))
my_choice = input('What characteristic do you want? (weight, height,id,) ' )

opponent_pokemon= random_pokemon()
print('The opponent pokemon is {}'.format(opponent_pokemon['name']))

player_choice = my_pokemon[my_choice]
opponent_choice = opponent_pokemon[my_choice]

if player_choice > opponent_choice:
  print('You Win!')
elif player_choice < opponent_choice:
  print('You Lose!')
else:
    print("It's a tie!")

run()
