### Нетология

#### Два проекта примера, в написании обоих приложений используется SwiftUI и Swift Playground:

##### 1.
<p align="center">
 <img src="https://github.com/maestrocrash/netologia/blob/main/Scrins/1.jpg">
</p>

```swift

import SwiftUI
import PlaygroundSupport

//Mini exaple
//Варианта создания массива
var array: [String]
var array1: Array<Int>
var array2 = [1,2,3]

//добавление элементов
array2.append(5)

//max example
struct TypePeople {
    var name: String
    var age: Int
    var growth: Float
    var city: String
    var favoriteColor: Color
    var icon: String
}

var arrayPeople: [TypePeople]

var p1 = TypePeople(name: "Michail", age: 28, growth: 178.9, city: "Saint-Petersburg",favoriteColor: .black, icon: "paperplane.fill")
var p2 = TypePeople(name: "Albina", age: 24, growth: 156.8, city: "Saint-Petersburg", favoriteColor: .purple, icon: "paperplane.fill")
var p3 = TypePeople(name: "Sveta", age: 49, growth: 163, city: "Salavat", favoriteColor: .red, icon: "house.fill")
var p4 =  TypePeople(name: "Evgeniy", age: 51, growth: 165, city: "Salavat", favoriteColor: .green, icon: "house.fill")
var p5 = TypePeople(name: "Evgeniy", age: 75, growth: 167, city: "Salavat", favoriteColor: .gray, icon: "house.fill")


arrayPeople = [p1, p2, p3]

//Вариант добавления элемента в массив
arrayPeople.append(TypePeople(name: "Valentina", age: 18, growth: 156, city: "Salavat", favoriteColor: .orange, icon: "house.fill"))

arrayPeople.append(p4)

arrayPeople.insert(p5, at: 0)


struct Preview: View {
    struct bodyView: View {
        
        var itemArray: TypePeople
        
        var body: some View {
            ZStack{
                Rectangle()
                    .fill(itemArray.favoriteColor)
                    .frame(width: 330, height: 180)
                    .cornerRadius(20)
                
                VStack {
                    HStack {
                        Image(systemName: itemArray.icon)
                            .resizable()
                            .frame(width: 20, height: 20)
                        Spacer()
                        
                        Text("\(itemArray.name)")
                            .foregroundColor(.white)
                            .font(.title)
                            .bold()
                        
                        Spacer()
                        
                        Text("\(itemArray.age) age")
                            .foregroundColor(.white)
                            .font(.system(size: 18))
                    }
                    
                    VStack {
                        HStack {
                            Text("City:".uppercased())
                                .underline()
                                .font(.system(size: 17, weight: .semibold))
                                
                            Text("\(itemArray.city)")
                                .font(.system(size: 24, weight: .bold))
                                
                            Spacer()
                        }
                        
                        Spacer()
                        
                        HStack {
                            Text("Growth:".uppercased())
                                .underline()
                                .font(.system(size: 17, weight: .semibold))
                            
                            Text("\(String(format: "%.1f", itemArray.growth))")
                                .font(.system(size: 24, weight: .bold))
                            
                            Spacer()
                        }
                    }
                    .padding(.top,15)
                    
                }
                .padding(.leading, 20)
                .padding(.trailing, 20)
                .frame(width: 310, height: 130)
            }
        }
    }
    
    var body: some View { 
        VStack {
            Text("Family")
                .font(.title)
                .bold()
                .padding(10)
        
            ScrollView {
                VStack {
                    bodyView(itemArray: arrayPeople[0])
                    bodyView(itemArray: arrayPeople[1])
                    bodyView(itemArray: arrayPeople[2])
                    bodyView(itemArray: arrayPeople[3])
                    bodyView(itemArray: arrayPeople[4])
                    bodyView(itemArray: arrayPeople[5])
                }
                
            }
        }
    }
}

PlaygroundPage.current.setLiveView(Preview())

for i in arrayPeople {
    print(i.name)
}

```

##### 2.

<p align="center">
 <img src="https://github.com/maestrocrash/netologia/blob/main/Scrins/2.jpg">
</p>

```swift
import SwiftUI
import PlaygroundSupport

enum typeCourse : String {
    case online = "онлайн"
    case offline = "оффлайн"
}

struct arrayType: Identifiable {
    var id = UUID()
    var image: UIImage
    var nameCourse: String
    var price: Int
    var data: Int
    var type: typeCourse
}

var array: [arrayType] = []

var courseSA : arrayType = arrayType(image: #imageLiteral(resourceName: "SA.png"), nameCourse: "Системный администратор", price: 58950, data: 12, type: .online ) 

var courseFront = arrayType(image: #imageLiteral(resourceName: "front.png"), nameCourse: "Frontend-разработчик с нуля", price: 77940, data: 15, type: .online)

var course1C = arrayType(image: #imageLiteral(resourceName: "1C.png"), nameCourse: "1С-разработчик", price: 56940, data: 7, type: .online)

var courseSec = arrayType(image: #imageLiteral(resourceName: "sec.png"), nameCourse: "Специалист по информационной безопасности", price: 77940, data: 12, type: .online)

var courseiOS = arrayType(image: #imageLiteral(resourceName: "ios.png"), nameCourse: "iOS-разработчик с нуля", price: 70740, data: 9, type: .online)

array = [courseSA, courseFront, course1C, courseSec]

array.append(courseiOS)



struct arrayCourse: View{
    
    var arrayCourse: [arrayType] = array
    
    var body: some View {
        
            List(arrayCourse) {item in 
                Image(uiImage: item.image)
                    .resizable()
                    .frame(width: 120, height: 120)
                    
                VStack(alignment: .leading) {
                    Text("\(item.nameCourse)")
                        .font(.system(size: 24, weight: .bold))
                        .padding(.bottom, 20)
                    HStack(alignment: .bottom){
                        Text("\(item.data) месяцев")
                            .underline()
                        Spacer()
                        Text("\(item.type.rawValue)")
                            .foregroundColor(.gray)
                        Spacer()
                        Text("\(item.price) ₽")
                            .font(.system(size: 20, weight: .bold))
                    }
                }
            }
    }
}

struct Preview: View {
    
    var body: some View {
        
        VStack {
            HStack {
                Image(uiImage: #imageLiteral(resourceName: "logo.png"))
                    .resizable()
                    .frame(width: 35, height: 35)
                
                Text("Нетология")
                    .font(.largeTitle)
            }
            .padding(.top, 25)
            
            Text("Программирование")
                .padding(.top, 10)
                .font(.title)
            
            arrayCourse()
        }
    }
}

PlaygroundPage.current.setLiveView(Preview())


```