<h1>HW4</h1>
<table>
  <tr>
    <td>
      <img src="https://raw.githubusercontent.com/ChenRongHsuan917/YZU-swiftui-1101548/main/hw4.gif">
     <h3>MyApp</h3>
      
 ```swift
    import SwiftUI

    @main
    struct MyApp: App {
        var body: some Scene {
            WindowGroup {
                ContentView()
            }
        }
    }
 ```

   <h3>ContentView</h3>
    
 ```swift
   import SwiftUI

struct ContentView: View { 
    var body: some View {
    VStack{ Text("元智地頭蛇")
            .font(.largeTitle)
            .fontWeight(.heavy)
            .foregroundStyle(.primary)
        TabView{ 
            Group{
                WelcomeView()
                Text("第一頁")
                    .tabItem {
                        Image(systemName: "rosette")
                        Text("Welcome")
                    }
                CourseListView()
                    .tabItem {
                        Image(systemName: "list.dash")
                        Text("Courses")
                    }
                Text("第三頁") 
                CardView()
                    .tabItem {
                        Image(systemName: "book")
                        Text("Learn")
                    } 
                SettingView()
                    .tabItem {
                        Image(systemName: "wrench")
                        Text("Setting")
                    } 
            }
            .toolbarBackground(Color.black,for:.tabBar)
            .toolbarBackground(.visible,for:.tabBar)
            }
        .tint(.yellow)
        }
    }
}

 ```
<h3>WelcomeView</h3>

```swift
    import SwiftUI

struct WelcomeView: View { 
    @AppStorage("UserName") var Username: String = ""
    var body: some View {
        VStack{
            Text(Username.isEmpty ? "" : Username)
                .font(.system(size: 30))
            Image("1")
                .resizable()
                .aspectRatio(contentMode: .fit) 
            Text("還不知道吃什麼嗎？\n       快來看看吧")
                .fontWeight(.heavy)
                .lineSpacing(20)
                .font(.system(size: 32.0))
                .foregroundColor(.white)
                .frame(width: 350, height: 150, alignment: .center)
            
        }
    } 
}

```

<h3>CourseListView</h3>

```swift
import SwiftUI

struct Course: Identifiable{
    var id = UUID()
    var name:String
    var image:String
    var description:String
}
var courses=[
    Course(name: "九嬸婆古早味冰", image: "九嬸婆冰",description:"add:興仁路二段81號\ncall:034525929"),
    Course(name: "邱記蔥肉餅", image: "蔥肉餅",description:"add:榮民路180號\ncall:0932865611"),
    Course(name: "正宗阿斌鹹酥雞 ", image: "正宗阿斌鹹酥雞",description:"add:榮民路165巷58號\ncall:034551195"),
    Course(name: "冰果Bingo 果汁舖", image: "果汁",description:"add:興仁路二段120號\ncall:034632260"),
    Course(name: "串串燒平價串燒", image: "燒烤",description:"add:興仁路二段184號ncall:0955141013")
]
struct BasicImageRow: View {
    var thisCourse: Course
    var body: some View {
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width:40,height:40)
                .cornerRadius(5)
            Text(thisCourse.name)
        }
    }
}

struct CourseDetailView: View {
    @Environment(\.presentationMode) var presentationMode
    var thisCourse: Course
    var body: some View {
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline, design: .rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }.overlay(
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label:{
                        Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                    .padding(.trailing,20)
                    .padding(.top,40)
                    Spacer()
                }
            }
        )}
}

struct CourseListView: View {
    @State var showDetailView = false
    @State var selectedCourse:Course?
    var body: some View {
        NavigationView{
            List(courses){ citem in
                BasicImageRow(thisCourse: citem)
                    .onTapGesture {
                        self.showDetailView = true
                        self.selectedCourse = citem
                    }
            }.sheet(item: self.$selectedCourse){ thisCourse in
                CourseDetailView(thisCourse: thisCourse)
            }
            .navigationTitle("課程列表")
        }
    }
}

```

<h3>CardView</h3>

```swift
  import SwiftUI

struct TermAndDescription: Identifiable{
    var id = UUID()
    var name:String
    var image:String
    var place:String
}

var myFood = [
    TermAndDescription(name: "九嬸婆古早味冰" ,image: "九嬸婆冰" ,place: "add:興仁路二段81號\ncall:034525929"),
    TermAndDescription(name: "邱記蔥肉餅" ,image: "蔥肉餅" ,place: "add:榮民路180號\ncall:0932865611"),
    TermAndDescription(name: "正宗阿斌鹹酥雞" ,image: "正宗阿斌鹹酥雞" ,place: "add:榮民路165巷58號\ncall:034551195"),
    TermAndDescription(name: "冰果Bingo 果汁舖" ,image: "果汁" ,place: "add:興仁路二段120號\ncall:034632260"),
    TermAndDescription(name: "串串燒平價串燒" ,image: "燒烤" ,place: "add:興仁路二段184號ncall:0955141013"),
]

struct CardView: View{
    @State var currentCard = Int.random(in: 0...4)
    var body: some View{
        VStack{
            Text("推薦餐廳")
                .font(.title)
                .offset(y: -50)
            VStack{
                Text(myFood[currentCard].name)
                    .font(.headline)
                //.padding(.all, 5)
                Image(myFood[currentCard].image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(myFood[currentCard].place)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
            }
            .frame(minWidth: 0, idealWidth: 100, maxWidth: 300, minHeight: 0, idealHeight: 100, maxHeight: 300 ,alignment: .center)
            .background(Color.gray)
            .onTapGesture{
                currentCard = Int.random(in: 0...4)
            }
            Text("抵達下一站")
                .offset(y: 50)
        }
    }
    }

  ```

  <h3>SettingView</h3>
  
   ```swift
      import SwiftUI

struct SettingView: View { 
    
    let displayFontType=[".default",".round",".monospaces","serif"]
    @State var displayFontselected = 0
    @State var IsDeepScheme = false
    @State var colorArray:Array = [255.0,255.0,255.0]
    @State var stepperValue = 0
    @State var sliderValue = 0.0
    @State var selectedDate = Date()
    @AppStorage("UserName") var UserName: String = ""
    var body: some View{
        NavigationView{
            Form(content: {
                Section(content: {
                    TextField("Please enter your name", text: $UserName)
                },header: {
                    Text("UserName")
                })
                Section(header:Text("Font settings"),content:{
                    Picker(selection: $displayFontselected,
                           label: Text("Font choice(\(displayFontselected))"),
                           content:{
                        ForEach(0..<displayFontType.count,
                                id:\.self,
                                content: {
                            Text(self.displayFontType[$0])
                        })
                    })
                })
                Section(header: Text("background style"),
                        content: {
                    Toggle(isOn: $IsDeepScheme,
                           label: {Text("dark(\(String(IsDeepScheme))")
                    })
                })
                Section(header: Text("Stepper")){
                    Stepper("Stepper(\(stepperValue))",
                            onIncrement:{stepperValue+=1},
                            onDecrement:{stepperValue-=1})
                }
                Section(header: Text("Slider(\(sliderValue,specifier:"%.2f"))")){
                    Slider(value:$sliderValue,in:0...1)
                }
                Section(header: Text("Date Picker")) {
                    DatePicker("Selected Date", selection: $selectedDate, displayedComponents: .date)
                        .datePickerStyle(GraphicalDatePickerStyle())
                        .onChange(of: selectedDate) { newValue in
                            print("Selected Date: \(newValue)")
                        }
                }
            })
            .navigationBarTitle("Settings")
        }
    }
}



   ```

   </td>
  </tr>
</table>
