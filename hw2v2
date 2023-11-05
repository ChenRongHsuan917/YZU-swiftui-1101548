<h1>HW2v2</h1>
<table>
  <tr>
    <td>
        <img src="https://raw.githubusercontent.com/ChenRongHsuan917/YZU-swiftui-1101548/main/hw2v2_pic.png">
        <img src="https://raw.githubusercontent.com/ChenRongHsuan917/YZU-swiftui-1101548/main/hw2v2_pic2.png">
    </td>
    <td>
      
```swift
  
    import SwiftUI

    struct ContentView: View {
        @State var playerScore: Int = 0
        @State var computerScore: Int = 0
        @State var gameType: String = "BO1"
        @State var isGameFinished: Bool = false
        var name = ["paper", "scissor", "rock"]
        var body: some View {
            VStack {

                //Menu
                Picker("Game Type", selection: $gameType) {
                    Text("BO1").tag("BO1")
                    Text("BO3").tag("BO3")
                    Text("BO5").tag("BO5")
                }
                .pickerStyle(SegmentedPickerStyle())
                .padding()
                
                //pic
                picView(imageName: name[computerScore])
                picView(imageName: name[playerScore])
                
                Text("Player: \(playerScore) vs Computer: \(computerScore)")
                    .font(.system(size: 30))
                    .padding(.all, 5)
                    .foregroundColor(.purple)
                
                if isGameFinished {
                    if (playerScore == 1 || (gameType == "BO3" && playerScore == 2) || (gameType == "BO5" && playerScore == 3) ){
                        Text("You Win")
                            .font(.system(size: 30))
                            .padding(.all, 5)
                    }
                    else if (computerScore == 1 || (gameType == "BO3" && computerScore == 2) || (gameType == "BO5" && computerScore == 3) ){
                        Text("You Lose")
                            .font(.system(size: 30))
                            .padding(.all, 5)
                    } 
                    else {
                        Text("Draw")
                            .font(.system(size: 30))
                            .padding(.all, 5)
                    }
                }
                HStack {
                    Button(action: {
                        playGame(playerSelection: 2)
                    }, label: {
                        Text("Rock")
                            .font(.system(size: 30))
                            .padding(.all, 10)
                            .frame(width: 100, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                    Button(action: {
                        playGame(playerSelection: 0)
                    }, label: {
                        Text("Paper")
                            .font(.system(size: 30))
                            .padding(.all, 10)
                            .frame(width: 100, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                    Button(action: {
                        playGame(playerSelection: 1)
                    }, label: {
                        Text("Scissor")
                            .font(.system(size: 30))
                            .padding(.all, 10)
                            .frame(width: 130, height: 50, alignment: .center)
                            .background(Color.purple)
                            .foregroundColor(.white)
                            .border(Color.purple, width: 5)
                            .cornerRadius(20)
                    })
                }
                
                  Button(action: {
                      playerScore = 0
                      computerScore = 0
                      isGameFinished = false
                  }, label: {
                      Text("Rester")
                          .font(.system(size: 30))
                          .padding(.all, 10)
                          .background(Color.teal)
                          .foregroundColor(.white)
                          .cornerRadius(10)
                  })
            }
        }
    
        func playGame(playerSelection: Int) {
            if !isGameFinished {
                let computerSelection = Int.random(in: 0...2)
        
                playerScore += (playerSelection + 1) % 3 == computerSelection ? 1 : 0
                computerScore += (computerSelection + 1) % 3 == playerSelection ? 1 : 0
                
                if (playerScore == 1 && gameType == "BO1") || (playerScore == 2 && gameType == "BO3") || (playerScore == 3 && gameType == "BO5") {
                    isGameFinished = true
                }
            }
        }
    }

    struct picView: View {
        var imageName: String
        var body: some View {
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode: .fit)
                .clipShape(Circle())
                .frame(width: 300)
        }
    }
```

  1101548_hw2v2 Playgrounds' code  </td>
  </tr>
</table>
