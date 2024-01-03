# DOM-Document Object Model
Bu repoda biz Javascriptdə ən əsas mövzulardan biri olan Document Object Model haqqında danışacıq. DOM haqqında bütün məlumatların olduğu repo kimi starlaya bilərsiniz.

## Sənəd Obyekt Modeli (DOM)

HTML sənədi JavaScript Obyekti kimi strukturlaşdırılmışdır. Hər bir HTML elementi onu manipulyasiya etməyə kömək edə biləcək fərqli xüsusiyyətlərə malikdir. JavaScript istifadə edərək HTML elementlərini əldə etmək, yaratmaq, əlavə etmək və ya silmək mümkündür. JavaScript istifadə edərək HTML elementinin seçilməsi CSS-dən istifadə etməklə seçilməyə bənzəyir. HTML elementini seçmək üçün biz teq adı, id, sinif adı və ya digər atributlardan istifadə edirik.

### Element əldə etmək

Biz JavaScript istifadə edərək artıq yaradılmış element və ya elementlərə daxil ola bilərik. Elementlərə daxil olmaq və ya əldə etmək üçün müxtəlif üsullardan istifadə edirik. Aşağıdakı kodun dörd _h1_ elementi var. _h1_ elementlərinə daxil olmaq üçün müxtəlif üsullara baxaq.

```html
<!DOCTYPE html>
  <html lang="en">
    <head>
      <title>Document Object Model</title>
    </head>
    <body>

     <h1 class='title' id='first-title'>First Title</h1>
     <h1 class='title' id='second-title'>Second Title</h1>
     <h1 class='title' id='third-title'>Third Title</h1>
     <h1></h1>

    </body>
  </html>
```

#### Teq adı ilə elementlərin alınması

**_getElementsByTagName()_**: sətir parametri kimi teq adını alır və bu üsul HTMLCollection obyektini qaytarır. HTMLCollection HTML elementlərinin obyekti kimi massivdir. Uzunluq xüsusiyyəti kolleksiyanın ölçüsünü təmin edir. Bu metoddan istifadə etdikdə biz hər bir fərdi element vasitəsilə indeksdən və ya sonra döngüdən istifadə edərək fərdi elementlərə daxil oluruq. HTMLCollection bütün massiv metodlarını dəstəkləmir, ona görə də biz forEach əvəzinə müntəzəm for loopundan istifadə etməliyik.

```js
// syntax
document.getElementsByTagName('tagname')
```

```js
const allTitles = document.getElementsByTagName('h1')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

#### Sinif adına görə elementlərin alınması

**_getElementsByClassName()_** metodu HTMLCollection obyektini qaytarır. HTMLCollection HTML elementlərinin siyahısı kimi massivdir. Uzunluq xüsusiyyəti kolleksiyanın ölçüsünü təmin edir. Bütün HTMLCollection elementləri arasında dövrə vurmaq mümkündür. Aşağıdakı nümunəyə baxın.

```js
//syntax
document.getElementsByClassName('classname')
```

```js
const allTitles = document.getElementsByClassName('title')

console.log(allTitles) //HTMLCollections
console.log(allTitles.length) // 4

for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i]) // prints each elements in the HTMLCollection
}
```

#### Elementi id ilə əldə etmək

**_getElementsById()_** tək HTML elementini hədəfləyir. Arqument olaraq id-i # olmadan keçirik.

```js
//syntax
document.getElementById('id')
```

```js
let firstTitle = document.getElementById('first-title')
console.log(firstTitle) // <h1>First Title</h1>
```

#### QuerySelector metodlarından istifadə etməklə elementlərin alınması

_document.querySelector_ metodu HTML və ya HTML elementlərini etiket adına, id və ya sinif adına görə seçə bilər.

**_querySelector_**: HTML elementini teq adı, id və ya sinfi ilə seçmək üçün istifadə edilə bilər. Teq adı istifadə edilərsə, yalnız birinci elementi seçir.

```js
let firstTitle = document.querySelector('h1') // select the first available h1 element
let firstTitle = document.querySelector('#first-title') // select id with first-title
let firstTitle = document.querySelector('.title') // select the first available element with class title
```

**_querySelectorAll_**: html elementlərini teq adı və ya sinfi ilə seçmək üçün istifadə edilə bilər. O, massiv metodlarını dəstəkləyən massiv kimi obyekt olan nodeList-i qaytarır. Hər nodeList elementləri arasında dövr etmək üçün **_for loop_** və ya **_forEach_** istifadə edə bilərik.

```js
const allTitles = document.querySelectorAll('h1') # selects all the available h1 elements in the page

console.log(allTitles.length) // 4
for (let i = 0; i < allTitles.length; i++) {
  console.log(allTitles[i])
}

allTitles.forEach(title => console.log(title))
const allTitles = document.querySelectorAll('.title') // the same goes for selecting using class
```

### Atribut əlavə etmək

HTML-in açılış etiketinə element haqqında əlavə məlumat verən atribut əlavə olunur. Ümumi HTML atributları: id, sinif, src, üslub, href, disabled, başlıq, alt. Dördüncü başlıq üçün id və sinif əlavə edək.

```js
const titles = document.querySelectorAll('h1')
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### setAttribute istifadə edərək atributun əlavə edilməsi

**_setAttribute()_** metodu istənilən html atributunu təyin edir. Atributun növü və atributun adı olan iki parametr alır.
Dördüncü başlıq üçün sinif və id atributunu əlavə edək.

```js
const titles = document.querySelectorAll('h1')
titles[3].setAttribute('class', 'title')
titles[3].setAttribute('id', 'fourth-title')
```

#### setAttribute olmadan atribut əlavə etmək

Atribut təyin etmək üçün normal obyekt təyini metodundan istifadə edə bilərik, lakin bu, bütün elementlər üçün işləyə bilməz. Bəzi atributlar DOM obyekt mülkiyyətidir və onlar birbaşa təyin edilə bilər. Məsələn, id və sinif

```js
//another way to setting an attribute
titles[3].className = 'title'
titles[3].id = 'fourth-title'
```

#### ClassList istifadə edərək sinif əlavə etmək

Sinif siyahısı metodu əlavə sinif əlavə etmək üçün yaxşı bir üsuldur. Bir sinif varsa, o, orijinal sinfi ləğv etmir, əksinə element üçün əlavə sinif əlavə edir.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.add('title', 'header-title')
```

#### Remove istifadə edərək sinifin silinməsi

Əlavə etmək kimi biz də sinfi elementdən silə bilərik. Biz müəyyən bir sinfi elementdən silə bilərik.

```js
//another way to setting an attribute: append the class, doesn't over ride
titles[3].classList.remove('title', 'header-title')
```

### HTML elementinə mətnin əlavə edilməsi

HTML açılış teqinin, bağlanış teqinin və mətn məzmununun quruluş blokudur. Biz _textContent_ və ya \*innerHTML xüsusiyyətindən istifadə edərək mətn məzmunu əlavə edə bilərik.

#### textContext istifadə edərək mətn məzmununun əlavə edilməsi

_textContent_ xüsusiyyəti HTML elementinə mətn əlavə etmək üçün istifadə olunur.

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'
```

#### innerHTML istifadə edərək Mətn Məzmununun əlavə edilməsi

Əksər insanlar _textContent_ və _innerHTML_ arasında çaş-baş qalırlar. _textContent_ HTML elementinə mətn əlavə etmək üçün nəzərdə tutulub, lakin innerHTML mətn və ya HTML elementi və ya elementləri uşaq kimi əlavə edə bilər.

##### Text Context

Biz mətnə *textContent* HTML obyekt xassəsini təyin edirik

```js
const titles = document.querySelectorAll('h1')
titles[3].textContent = 'Fourth Title'
```

##### Inner HTML

Biz ana elementi əvəz etmək və ya tamamilə yeni child content-i dəyişdirmək istədiyimiz zaman innerHTML xassəsindən istifadə edirik.
Təyin etdiyimiz dəyər HTML elementləri sətri olacaq.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul></ul>
    </div>
    <script>
    const lists = `
    <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>`
  const ul = document.querySelector('ul')
  ul.innerHTML = lists
    </script>
  </body>
</html>
```

innerHTML xassəsi ana elementin bütün uşaqlarını silməyə də imkan verə bilər. RemoveChild() funksiyasından istifadə etmək əvəzinə aşağıdakı metodu tövsiyə edərdim.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>JavaScript for Everyone:DOM</title>
  </head>
  <body>
    <div class="wrapper">
        <h1>Asabeneh Yetayeh challenges in 2020</h1>
        <h2>30DaysOfJavaScript Challenge</h2>
        <ul>
            <li>30DaysOfPython Challenge Done</li>
            <li>30DaysOfJavaScript Challenge Ongoing</li>
            <li>30DaysOfReact Challenge Coming</li>
            <li>30DaysOfFullStack Challenge Coming</li>
            <li>30DaysOfDataAnalysis Challenge Coming</li>
            <li>30DaysOfReactNative Challenge Coming</li>
            <li>30DaysOfMachineLearning Challenge Coming</li>
        </ul>
    </div>
    <script>
  const ul = document.querySelector('ul')
  ul.innerHTML = ''
    </script>
  </body>
</html>
```

### Style əlavə etmək

#### Stil Rənginin əlavə edilməsi

Gəlin başlıqlarımıza bəzi style-lar əlavə edək. Elementin cüt indeksi varsa, ona yaşıl rəng veririk, yoxdursa qırmızı.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.color = 'green'
  } else {
    title.style.color = 'red'
  }
})
```

#### Stil arxa plan rənginin əlavə edilməsi

Gəlin başlıqlarımıza bəzi style-lar əlavə edək. Elementin cüt indeksi varsa, ona yaşıl rəng veririk, yoxdursa qırmızı.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.backgroundColor = 'green'
  } else {
    title.style.backgroundColor = 'red'
  }
})
```

#### Stil Şrift Ölçüsünün əlavə edilməsi

Gəlin başlıqlarımıza bəzi style-lar əlavə edək. Elementin cüt indeksi varsa, ona 20px, digər halda 30px veririk.

```js
const titles = document.querySelectorAll('h1')
titles.forEach((title, i) => {
  title.style.fontSize = '24px' // all titles will have 24px font size
  if (i % 2 === 0) {
    title.style.fontSize = '20px'
  } else {
    title.style.fontSize = '30px'
  }
})
```

Qeyd etdiyiniz kimi, JavaScript-də istifadə etdiyimiz zaman css-in xassələri camelCase olacaq. Aşağıdakı CSS xassələri fon rəngindən backgroundColor-a, font-size fontSize-ə, font-family fontFamily-ə, margin-bottom-dan marginBottom-a dəyişir.

Okay, mənim canavar tələbələrim, siz demək olarki, DOM-da elementlər haqqında hər məlumata sahibsiniz. Növbəti dərslər daha da maraqlı olacaq :D. DOM Manipulyasiyası və EventListener-lar ilə daha üst səviyyəyə çıxacağıq.
