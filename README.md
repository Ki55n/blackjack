# blackjack



from random import shuffle

def deck():
    deck = []
    for suit in ['H', 'S', 'D', 'C']:
        for rank in ['A', '2', '3', '4', '5', '6', '7', '8', '9','T', 'J', 'Q', 'K']:
            deck.append(suit+rank)


    shuffle(deck)

    return deck

def pointCount (myCards):
    myCount = 0
    aceCount = 0
    for i in myCards:
        if (i[1] == 'J' or i[1] == 'Q' or i[1] == 'K' or i[1] == 'T'):
            myCount+= 10

        elif(i[1] != 'A'):
            myCount+= int(i[1])

        else:
            aceCount+=1
    if (aceCount ==1 and myCount >= 10):
        myCount += 11
    elif (aceCount != 0):
        myCount += 1
    return myCount



def create_Player_Hands (myDeck):
    dealer_Hand = []
    player_Hand = []
    dealer_Hand.appned(myDeck.pop())
    dealer_Hand.appned(myDeck.pop())
    dealer_Hand.appned(myDeck.pop())

    while(pointCount(dealer_Hand) <= 16):
        dealer_Hand.append(myDeck.pop())


    return [dealer_Hand, player_Hand]

game = ""
myDeck = deck()
hands = create_Player_Hands(myDeck)
dealer = hands [0]
player = hands [1]

while(game != "exist"):
    dealerCount = pointCount(dealer)
    playerCount = pointCount(player)

    print("Dealer has:")
    print(dealer[0])

    print("Player You Have:")
    print(player)

    if (playerCount == 21):
        print("Blackjack player Win!")
        break
    elif(playerCount == 21):
        print("Player Loss" + str(playerCount) + " points Dealer wins! ")
        break

    elif (dealerCount > 21):
        print("Dealer Loss with" + str(dealerCount) + " points player wins! ")

    game = input("What would you like to do ? H: hit me , S: Stand? ")

    if (game == 'H'):
        player.append(myDeck.pop)
    elif (playerCount > dealerCount):
        print(" Player Win with " + str(playerCount) + " points ")
        print(" Dealer has! " + str(dealer) + " or " + str(dealerCount) + " points ")
        break

    else:
        print("Dealer has! ")
        print(" Dealer has! " + str(dealer) + " or " + str(dealerCount) + " points ")
        break







    









