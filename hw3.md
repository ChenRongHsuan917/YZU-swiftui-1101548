<h1>HW3</h1>
<table>
  <tr>
    <td>
       <img src="https://raw.githubusercontent.com/ChenRongHsuan917/YZU-swiftui-1101548/main/IMG_2586.jpeg">
    </td>
    <td>
      
```swift
    import SwiftUI
import UIKit

struct ContentView: View {
    var body: some View {
        VStack{
            TitleView()
            HStack{
                FruitView(imageName: "bandaids")
                FruitView(imageName: "HormoneBoy")
                FruitView(imageName: "SCAR")
            }
            ZStack{
                //im3View() 
                HStack{
                    FruitView(imageName: "星夜")
                    FruitView(imageName: "拾穗")
                }
                Text("繪於：1857")
                    .font(.system(size: 10))
                    .foregroundColor(.yellow)
                    .padding(.all,5)
                    .background(Color.black)
                    .opacity(0.7)
                    .offset(x:150 , y: 40)
            }
            HStack{
                FruitView(imageName: "韓韶禧")
                FruitView(imageName: "舒華")
                FruitView(imageName: "IU")
            }
        }
    }
} 

struct TitleView: View{
    var body: some View{
        VStack(alignment:.center, spacing:2){
            Text("Hsuan's")
                .italic()
                .font(.largeTitle)
                .foregroundColor(Color(red: 225/255,green: 168/255,blue:142/255))
        }
        .font(.system(size:30)); 
        Text("收藏櫃")
            .italic()
            .font(.title)
            .foregroundColor(Color(red: 225/255,green: 168/255,blue:162/255))
    }
}
struct FruitView: View {
    var imageName:String
    var body: some View {
        VStack{ 
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode:.fit)
                .frame(width: UIScreen.screenWidth/2-20, alignment: .center)
                .aspectRatio(contentMode:.fit)
                .padding(.all, 15)
            Text(imageName.capitalized)
                .fontWeight(.bold)
                .font(.custom("Caveat", size: 20))
        
        }
        .onAppear(perform: {
            let fontURL = Bundle.main.url(forResource: "Caveat-VariableFont_wght", withExtension: "ttf")!as CFURL
            CTFontManagerRegisterFontsForURL(fontURL, CTFontManagerScope.process, nil)
        })
        .italic()
        .frame(minWidth: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealWidth: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxWidth: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, minHeight: /*@START_MENU_TOKEN@*/0/*@END_MENU_TOKEN@*/, idealHeight: /*@START_MENU_TOKEN@*/100/*@END_MENU_TOKEN@*/, maxHeight: /*@START_MENU_TOKEN@*/.infinity/*@END_MENU_TOKEN@*/, alignment: /*@START_MENU_TOKEN@*/.center/*@END_MENU_TOKEN@*/)
    } 
}

extension UIScreen{
    static let screenWidth = UIScreen.main.bounds.size.width
    static let screenHeight = UIScreen.main.bounds.size.height
    static let screenSize = UIScreen.main.bounds.size
}

```

  1101548_hw3 Playgrounds' code  </td>
  </tr>
</table>
