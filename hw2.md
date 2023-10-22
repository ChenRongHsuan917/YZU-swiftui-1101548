import SwiftUI

struct ContentView: View{
    @State var user:Int = 0
    @State var num :Int = 0
    var body: some View{
        VStack{
            //let com_num = 0;
            //let user_num = 0;
            let listc = ["🖥️","✌️","✊","🤚","🖥️🏳️","🖥️🪞","🖥️🥇"]
            let list = ["🐰","✌🏻","✊🏻","🤚🏻","🙏🏻🧎‍♀️","🪞😃","🥇"]
            let listxt=["PUSH THE BUTTON TO START THE GAME","Win! Good","Loser Haha","Battle to a draw"]
            Text(String(listc[num]))
                .padding(.all,10)
                .font(.system(size:100))
                .frame(width:300,height:120,
                       alignment: .center)
            Text(String(list[user]))
                .padding(.all,10)
                .font(.system(size:100))
                .frame(width:300,height:120,
                       alignment: .center)
            /*computer → user
             lose:       win: 
             0 →2 3     0 →1 5
             1 →0 3.    1 →2 5 
             2 →1 3.    2 →0 5
             3 → win.   3 →win
             4 → tie.   4 →tie
             5 →lose.   */
            if(num == 0 && user == 0){
                Text(String(listxt[0]))
                    .foregroundColor(.red)
                    .padding(.all,10)
                    .font(.system(size:20))
                    .frame(width:500,height:120,
                           alignment: .center)
            }
            else if(num==user) {
                Text(String(listxt[3]))
                    .foregroundColor(.secondary)
                    .padding(.all,10)
                    .font(.system(size:40))
                    .frame(width:500,height:120,
                           alignment: .center)
            }
            else if(num==4||user==6){
                Text(String(listxt[1]))
                    .foregroundColor(.green)
                    .padding(.all,10)
                    .font(.system(size:70))
                    .frame(width:500,height:120,
                           alignment: .center)
            }
            else if(num==6||user==4){
                Text(String(listxt[2]))
                    .foregroundColor(.orange)
                    .padding(.all,10)
                    .font(.system(size:70))
                    .frame(width:500,height:120,
                           alignment: .center)
            }
            else if(num==5||user==5) {
                Text(String(listxt[3]))
                    .foregroundColor(.secondary)
                    .padding(.all,10)
                    .font(.system(size:40))
                    .frame(width:500,height:120,
                           alignment: .center)
            }
            else if(num==1){
                if(user==3){
                    Text(String(listxt[2]))
                        .foregroundColor(.orange)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
                else if(user==2){
                    Text(String(listxt[1]))
                        .foregroundColor(.green)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
            }
            else if(num==2){
                if(user==1){
                    Text(String(listxt[2]))
                        .foregroundColor(.orange)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
                else if(user==3){
                    Text(String(listxt[1]))
                        .foregroundColor(.green)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
            }
            else if(num==3){
                if(user==2){
                    Text(String(listxt[2]))
                        .foregroundColor(.orange)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
                else if(user==1){
                    Text(String(listxt[1]))
                        .foregroundColor(.green)
                        .padding(.all,10)
                        .font(.system(size:70))
                        .frame(width:500,height:120,
                               alignment: .center)
                }
            }//end →
            Button(action:{
                user = Int.random(in: 1..<7)
                num = Int.random(in: 1..<7)
            }, label:{
                Text("Start!")
                    .italic()
                    .padding(.all,10)
                    .font(.system(size:50))
                    .frame(width:300,height:100,
                           alignment: .center)
                    .background(Color.teal)
                    .foregroundColor(.white)
                    .cornerRadius(9)
            })//button end
            //Text("比分 \(com_num) vs \(user_num)")
        }
    }
}

