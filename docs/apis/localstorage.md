# Web Storage API
Web Storage API 提供机制， 使浏览器能以一种比使用Cookie更直观的方式存储键/值对。


Web Storage API 继承于Window 对象,并提供两个新属性  

Window.sessionStorage — 提供对当前域的会话

Window.localStorage — 提供对本地Storage对象的访问

调用其中任一对象会创建 Storage 对象，通过 Storage 对象，可以设置、获取和移除数据项。

## localStorage是什么

```javascript
const cityForm = document.querySelector('form')

const card = document.querySelector('.card')
const details = document.querySelector('.details')
const time = document.querySelector('img.time')
const icon = document.querySelector('.icon img')

//333333333333 CREATE updateUI() START/////////////
const updateUI = (data) => {
    console.log(data)
    console.log(data.weather.WeatherIcon)
    // const cityObj = data.cityObj
    // const weatherObj = data.weatherObj
    const {cityObj, weatherObj} = data //5 destructuring

    details.innerHTML = `
        <h5 class="my-3">${cityObj.EnglishName}</h5>
        <div class="my-3">${weather.WeatherText}</div>
        <div class="display-4 my-4">
        <span>${weather.Temperature.Metric.Value}</span>
        <span>&deg;C</span>
        </div>`
    let iconSrc = `img/icons/${weather.WeatherIcon}.svg`
    icon.setAttribute('src', iconSrc)
    //the night/day img
    let timeSrc = weather.IsDayTime ? 'img/day.svg' :'img/night.svg'
    time.setAttribute('src', timeSrc) //7.setAttribute()
    //revmoe the d-none
    if(card.classList.contains('d-none')){ //4.containers includes()
        card.classList.remove('d-none')
    }
}
//333333333333 CREATE updateUI() END/////////////

//222222222222.create handleFunction START///////////////
const handleCity = async (city) => {
    const cityObj = await getCity(city)
    const weatherObj = await getWeather(cityObj.Key)

    return {
        cityObj, //3. object shorthand notation
        weatherObj
    }
}
////////////2.create handleFunction END///////////////

//1111111111. handle a submit event START////////////
cityForm.addEventListener('submit', e => {
    e.preventDefault()
    const city = cityForm.city.value.trim() //1.form.city
    cityForm.reset() //2.reset()


    handleCity(city)
        .then( data => {
            console.log(111)
            updateUI(data)
        })
        .catch( error => { console.log( error )})

    localStorage.setItem('city',city)
})
//1111111111. handle a submit event END//////////////

if(localStorage.getItem('city')){
    handleCity(localStorage.getItem('city'))
    .then(data => updateUI(data))
    .catch( err => console.log(err))
}

```