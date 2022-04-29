<script lang="ts">
 export let weather;
</script>



<div class="col-12 col-md-6 animate__animated animate__fadeInUp">
    <h1>
        <img
            src={`http://openweathermap.org/img/wn/${weather.weather[0].icon}@2x.png`}
            alt={weather.name}
            class="bg-secondary"
        />
        {weather.main.temp}ºC
    </h1>
    <h4>
        City: <span class="fw-bold"
            >{weather.name}, {weather.sys.country}</span
        >
    </h4>
    <h4>
        Weather: <span class="fw-bold"
            >{weather.weather[0].description}</span
        >
    </h4>
</div>
<div class="col-12 col-md-6 mt-4 animate__animated animate__fadeInUp">
    <h4>
        Max Temperature: <span class="fw-bold text-danger font"
            >{weather.main.temp_max}ºC</span
        >
    </h4>
    <h4>
        Min Temperature: <span class="fw-bold text-primary font"
            >{weather.main.temp_min}ºC</span
        >
    </h4>
</div>

<style>
    h4{
        font-size: 20px;
    }
    .font{
        font-size: 25px;
    }
</style>