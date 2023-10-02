<h1>HW1</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/ChenRongHsuan917/YZU-swiftui-1101548/main/hw1_pic.png">
    </td>
    <td>
      
```swift
        import SwiftUI
  
        struct ContentView: View {
          var body: some View {
          Image("917_")
              .resizable()
              .frame(width: 500, height: 400, alignment: .center/*@END_MENU_TOKEN@*/)
              .clipShape(Circle())
              .opacity(0.9)
              .aspectRatio(contentMode: .fill)
              .overlay (
                  Image(systemName: "bolt.heart.fill")
                      .fontWeight(.bold)
                      .frame(width: 120, height: 320, alignment: .topTrailing)
                      .foregroundColor(.pink)
              )
              .overlay(
                  Text("1101548陳蓉萱")
                      .fontWeight(.heavy)
                      .lineSpacing(5.0)
                      .font(.system(size: 16.0))
                      .foregroundColor(.brown)
                      .frame(width: 250, height: 100, alignment: .center )
                      .cornerRadius(30.0)
                  ,
                  alignment: .topTrailing
              )
              .overlay(
                  Text("          Chill Hight Hight , \nHang on to your dream")
                      .fontWeight(.regular)
                      .font(.system(size: 20))
                      .foregroundColor(.brown)
                      .position(x: 325, y: 100)
              )
            }
          }

```

    </td>
  </tr>
</table>
