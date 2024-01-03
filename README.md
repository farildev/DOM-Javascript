# DOM-Document Object Model
Bu repoda biz Javascriptdə ən əsas mövzulardan biri olan Document Object Model haqqında danışacıq. DOM haqqında bütün məlumatların olduğu repo kimi starlaya bilərsiniz.


- [Sənəd Obyekt Modeli (DOM) - 1-ci Gün](#document-object-model-dom---day-1)
- [Getting Element](#getting-element)
- [Elementlərin teq adına görə alınması](#elementlərin etiket adına görə alınması)
- [Sinif adına görə elementlərin alınması](#sinf adına görə elementlərin alınması)
- [İd ilə element əldə edilir](#getting-an-element-by-id)
- [QuerySelector metodlarından istifadə edərək elementlərin əldə edilməsi](#getting-elements-by-using-queryselector-methods)
- [Atribut əlavə edilir](#adding-atribut)
- [setAttribute istifadə edərək atribut əlavə edilir](#adding-attribute-using-setattribute)
- [setAttribute olmadan atribut əlavə edilir](#adding-attribute-without-setattribute)
- [ClassList istifadə edərək sinif əlavə etmək](#adding-class-using-classlist)
- [Sildən istifadə edərək sinif silinir](#removing-class-using-remove)
- [HTML elementinə mətnin əlavə edilməsi](#html elementinə mətnin əlavə edilməsi)
- [Mətn məzmunundan istifadə edərək mətn məzmununun əlavə edilməsi](#mətn məzmunundan istifadə edərək mətnin əlavə edilməsi)
- [innerHTML istifadə edərək Mətn Məzmununun əlavə edilməsi](#innerhtml-dən istifadə edərək mətnin əlavə edilməsi)
- [Mətn Məzmunu](#text-content)
- [Daxili HTML](#inner-html)
- [Stil əlavə edilir](#adding-style)
- [Stil Rənginin Əlavə Edilməsi](#adding-style-color)
- [Stil Arxa Fon Rənginin Əlavə Edilməsi](#adding-style-fon-color)
- [Stil Şrift Ölçüsünün Əlavə Edilməsi](#adding-style-font-size)


## Sənəd Obyekt Modeli (DOM)

HTML sənədi JavaScript Obyekti kimi strukturlaşdırılmışdır. Hər bir HTML elementi onu manipulyasiya etməyə kömək edə biləcək fərqli xüsusiyyətlərə malikdir. JavaScript istifadə edərək HTML elementlərini əldə etmək, yaratmaq, əlavə etmək və ya silmək mümkündür. Aşağıdakı nümunələri yoxlayın. JavaScript istifadə edərək HTML elementinin seçilməsi CSS-dən istifadə etməklə seçilməyə bənzəyir. HTML elementini seçmək üçün biz teq adı, id, sinif adı və ya digər atributlardan istifadə edirik.

### Element əldə edilir

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
