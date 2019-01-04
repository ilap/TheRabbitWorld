 # The Rabbit World

There is a Rabbit world which contains RabbitCities.
The cities are similar accross the rabbit world.

 # The Rabbit City

A rabbit city can be small, at least with one house with at least one rabbit, or big (max. 100 houses and max. 20 Rabbits in a house).

 # The Rabbit Houses

In the city there are RabbitHouses.
These houses can have only three shapes: triangle, square and rectangle.
They have colors (currently 4 and max. 100),
Houses with the same color in a city can only have different shapes.
This means that shaped houses are uniq in color, therefore there cannot be two YellowTriangle house in a city,
but can have infinit number of different colored houses.

 # The Rabbits

One or more Rabbits (theoritically infinite, but realisticly max 10-20) can live in each house.

Each house tracks how many rabits lived there. E.g. 42 lived in a house life, but currently there is only one is living.
The rabits have breeds (currenlty they have 4 type of breeds max 20) in the whole world, and they do not have any benefit to the other breeds.

Rabbits cannot lay colorful eggs but receive them as gift from other rabbits.
The number of eggs are existed from the beginning of the RabbitWorld.

 # The Eggs

The Eggs are gifts that can be sent from any rabbit to an other rabbit that lives in the same or a similar house.

In the whole world, the eggs have colors and shapes that are specific to their house (E.g. yellow eggs with triangle sign on it for the `YellowTriangle` houses) and therefore they cannot be send to any other rabbits that are living in a differently shaped or colored house.

 # The Rabbit World Global Eggs Delivery Services

The `Global Eggs Delivery Service` deliver any house specific eggs from any rabbit to any other rabbits that are live in the __same__ or __similar type__ of houses. This is required as the service will have to keep all the history of the Rabbit world.

E.g. `YellowTriangleGlobalEggsDeliveryService` deliver the YellowTriangleHouses' eggs from and for the rabbits that are living in the `Yellow Triangle houses` in the Rabbit world. 

Sending eggs has its price, and different type of eggs delivery can have different price defined in the relevant `GlobalEggsDeliverService`.

They have a minimum delivery fee defined. But, this price can increase that is related to the number of eggs to be sent.
These price calculations are defined in the relevant `GlobalEggsDeliveryService` depends on the number of the eggs to be sent.

Also, it can happen that the same colored eggs delivery fees are same for the different colored (but same shaped) `GlobalEggsDeliveryService`-s.

These delivery servies are responsible for checking (their shapes, colors and numbers) and sending the eggs from one rabbit to any rabbit in the rabbit world.

The `GlobalEggsDeliveryService` have the history of all gift givings.

Also, they have statuses whether they can deliver any eggs or not.

How this `GlobalEggsDeliveryServices` send and receive the eggs are not relevant and not in this scope of this `Tale`.

# Houses' EggsHistory

Every house wants to keep track of every eggs delivery (sending and receiving eggs from/to rabbits).

They are also interested in that how many Rabbits are lived in that house since they're firstly built and that how many eggs its rabbits have.

A house's local eggs delivery history can have some extra information on each delivery, like "From Love from Roger Bunny to my oldest friend Bugs Bunny".

These additional pieces of information are not kept in
the `GlobalEggsDeliveryService` as they are very bureaucratic and they just store very different and limited information.

 # Business rules:

There is a rabbit city called EasterRabbitCity.
In that city there's a `BugsBunnyHouse', and we're interested in only this house.

- Rabits can be born and reborn anytime by the City God which is an unkown and unseen entity (Every city has its CityGod),  but only if all other living rabits in that house have received at least one egg from any other rabbits from the same or other similar houses in the world.
- If the rabbits is reborn it's eggs giving history is also can be retrieved.
- The house must keep track of the new arrives of rabbits.
  - Means if the lived rabbits is 99, then it must be track that it's the 100th rabbit in the house.
- Any rabbit can die at any time, by wish of that God, but their eggs giving history must be kept locally (with additional info) in the house and globally in the `GlobalEggsParcelService` (only bare metal info).
- Any rabbit can be silenced at any time, which means that the god cannot send any eggs from that rabbit, but receive until they're unsilenced.
- The CityGod can send any eggs from a rabbit to an other rabbit in the world.
- The CityGod can operate (check rabbits, rabbits' eggs, houses, history etc.) only on one house at a time, but he can select any other house in the same city any time. But, he must work on the selecte house only. 
  - This means that he can send egg only from the chosen house' rabbit to an other rabbit, but can receive delivery arrived into the city notifications from any houses in the city.


- Any house can be destroyed any time, and that means any local history (detailed history) will be destroyed (and cannot be fully reconstructed if the house is rebuilt again), but the global history (minimal info) will be kept forever.
- It also means that the rabbits history is not reconstructed for historical reason.
- The local eggs history can be reconstructed from the global history (means every additional info were in the local history are lost)

- The houses has an address
- The rabbits have identity which is uniq in the world, 
- One rabbit can only belong to one house (address),

# Future Features

- The Rabbits sometimes can move to similar houses in other cities, but never to any other type of houses.
- The rabbits sometimes can duplicate themselves and live in two or more houses at the same time and when they die on one city then can live simultanously in the other city.


``` dart
class House {
  int Id;
}


class Rabbit {
  int Id;
  int houseLivesInId;
  int name;
}

class Eggs {
  int numberOfEggs;
}

class EggsGivingLocalHistory {
  int HistoryID.
  Rabbit from;
  Rabbit to;
  Egg eggs;
  String lovelyMessage;
  DateTime sent;
  Status status; // created, sent, delivered or failed, for simplicity
}

// This history is very different than the local one
class EggsGivingGlobalHistory {

}
```


