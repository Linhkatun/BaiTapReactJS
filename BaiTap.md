//bài 21: tính tổng tất cả các số của mảng
var numbers=[2,5,6,2,5,9,5,3];
function totalNumbers(){
    var total=0;
    for(var i=0; i<numbers.length; i++){
        total+=numbers[i];
    }
    document.writeln("bài 21: total= ",total);
}
totalNumbers();

//bài 22: tìm số lớn nhất, nhỏ nhất và trung bình trong mảng này

function max(){
    var max=numbers[0];
    for(var i=0 ; i<numbers.length; i++){
        if(max<numbers[i]){
            max=numbers[i];
        }
    }
    document.writeln("bài 22: Max= ",max);
}
max();

function min(){
    var min = numbers[0];
    for(var i=0 ; i<numbers.length; i++){
        if(min>numbers[i]){
            min=numbers[i];
        }
    }
    document.writeln(" Min= ",min);
}
min();

function trungbinh(){
    var dem=0;
    for(var i=0; i<numbers.length; i++){
        dem++;
    }
    var trungbinh=numbers.reduce((a,b)=>(a+b))/dem;
    document.writeln("trung bình= ",trungbinh);
}
trungbinh();
//bài 23: tìm số có tần số xuất hiện nhiều nhất

function timSoXuatHienNhieuNhat(){
    var array=numbers.sort();
    var dem=0;
    var hienthi=1;
    for(var i=0; i<array.length-1;i++){
        if(array[i]=array[i+1]){
            hienthi++;
        }
        else{
            if(hienthi>=dem){
                dem=hienthi;
                hienthi=1;
            }
            else{
                hienthi=1;
            }
        }
    }
    document.writeln("số xuất hiện nhiều nhất là:",dem);
}
timSoXuatHienNhieuNhat();

//bài 24: Cho một mảng là một tập các số nguyên dương, lọc ra một bảng b gồm tất cả các số là số nguyên tố? (Dùng filter)

var b=[];
function songuyen(numbers){
    var count=1;
    for(var i=0; i<numbers.length; i++){
        if(numbers[i]>=2){
            for(j=2; j<=numbers[i];j++){
                if(numbers[i]%j==0){
                    count++;
                }
            }
            if(count<=2){
                b.push(numbers[i]);
                count=1;
            }
            else{
                count=1;
            }
        }
    }
    document.write("bai24:",b);
}
songuyen();

//bài 25:Cho một mảng là một tập các số nguyên dương, hãy tạo một mảng b là tập hợp bình phương của các số trong mảng a
function bai25() {
    var b = [];

    for ( var i = 0; i < numbers.length; i++) {
        b.push(numbers[i]**2);
    }

    document.write("bai25:",b);
}
bai25();
function ex26() {
    var a = [1,3,4,7,9,11,3];
    var b = Number(prompt("input a number: "));
    var larger = []; //những số lớn hơn b;
    var smaller = []; //những số nhỏ hơn b;
    var result = [];
    for (var i = 0; i < a.length; i++) {
        if (b > a[i]) {
            smaller.push(a[i]);
        } else if (b < a[i]) {
            larger.push(a[i]);
        } else if ( b = a[i]) {
            console.log(b + " có xuất hiện trong chuỗi tại index: " + i);
        }
    }
    if (smaller.length == 0) {
        console.log("Giá trị gần nhất là: " + Math.min.apply(Math, larger));
    } else if (larger.length == 0) {
        console.log("Giá trị gần nhất là: " + Math.max.apply(Math, smaller));
    } else if (smaller.length != 0 && larger.length != 0) {
        result.push(Math.max.apply(Math, smaller), Math.min.apply(Math, larger));
        console.log("Giá trị gần nhất là: " + result);
    }
}

function ex27() {
    var students = [
        {
            id: "T3HXX1",
            firstName: "linh",
            lastName: "nguyEn ThI"
        },
        {
            id: "T3HXX2",
            firstName: "yeS",
            lastName: "haHA"
        },
        {
            id: "T3HXX5",
            firstName: "hIgH",
            lastName: "aS a Kite" 
        }];

    var results = students.filter(student => student.firstName.length >= 3)
        .map(
            student => {
                return {
                    id: student.id,
                    firstName: student.firstName.toLowerCase().replace(student.firstName[0], student.firstName[0].toUpperCase()),
                    lastName: student.lastName.toLowerCase().split(" ").map(item => item[0].toUpperCase() + item.slice(1)).join(" ")
                }});

    console.log(results);
}

function ex28() {
    var students = [
        {
            id: "T3HXX1",
            firstName: "Tung",
            lastName: "Doan Hoang"
        },
        {
            id: "T3HXX2",
            firstName: "No",
            lastName: "Shit Motherfucker"
        },
        {
            id: "T3HXX5",
            firstName: "High",
            lastName: "As a Kite" 
        },
        {
            id: "T3HXX1",
            firstName: "No",
            lastName: "Shit Cunt"
        }
    ]
    
    var results = students.filter(student => student.lastName.split(" ")[0] === "Shit");
    console.log(results);
}

function ex29() {
    var students = [
        {
            id: "T3HXX1",
            firstName: "Tung",
            lastName: "Doan Hoang"
        },
        {
            id: "T3HXX2",
            firstName: "No",
            lastName: "Shit Motherfucker"
        },
        {
            id: "T3HXX5",
            firstName: "High",
            lastName: "As a Kite" 
        },
        {
            id: "T3HXX1",
            firstName: "No",
            lastName: "Shit Cunt"
        }
    ];
    
    var sortByName = students.slice(0)
        .sort(
            function(a,b) {
                var x = a.firstName;
                var y = b.firstName;
                if (x < y) {
                    return -1;
                } else if (x > y) {
                    return 1;
                } else {
                    return 0;
                }});
    console.log(sortByName);
}

function ex30() {
    var numbers = [1,2,3,4,5,6,7,8,9,9,8,7,6,5,4,3,2,1]
    // var numbers =[1,1,1,1,1,1,]
    var resultarr = []

    for (var i = 0; i < numbers.length; i++) {
        if (numbers[i] < Math.max(...numbers)) {
            resultarr.push(numbers[i])
        }
    }
    var result = Math.max(...resultarr)
    if (result === -Infinity) {
        console.log(-1)
    } else {
        console.log(result)
    }
}

function ex31() {
    var array = [9,1,8,3,4,15,19]
    var z = 18
    for (var a = 0; a < array.length; a++) {
        for (var b = a + 1; b < array.length; b++) {
            for (var c = b + 1; c < array.length; c++) {
                if (z == array[a] + array[b] + array[c]) {
                    var result = "yes";
                    break;
                }
            }
        }
    }

    if (result != "yes") {
        console.log("no")
    } else {
        console.log(result)
    }
}
