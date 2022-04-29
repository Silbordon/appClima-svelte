<script lang="ts">
import type { WeatherDataInterface } from "../interfaces/Weather";

import ErrorAlert from "./ErrorAlert.svelte";

import Loading from "./Loading.svelte";
import WeatherData from "./WeatherData.svelte";

    const key = "6c6e522e3a56ca5581e354ccd1bc03be";
    let city = "";
    

    const getWeatherData = async (city: string = "argentina") => {
        let urlBase=`https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${key}`;

        
        if (city.trim() === "") {
            throw new Error(
                "It is necesary to fill the fields with valid information"
            );
        }

        const res:Response = await fetch(urlBase);
        if(res.ok === false){
            throw new Error("City does not exist");
        }
        
        const data:WeatherDataInterface = await res.json();
    
        return data;
    };

    let promise = getWeatherData();

    const handlerSubmit = () => {
        promise = getWeatherData(city);
        city = "";
    };
</script>

<div class="container">
    <div class="row">
        <div class="col-12 mb-4">
            <form class="form-container" on:submit|preventDefault={handlerSubmit}>
                <label>
                    City: <input
                        bind:value={city}
                        type="text"
                        class="form-control"
                    />
                </label>
                <button type="submit" class="btn btn-info">Search</button>
            </form>
        </div>

        {#await promise}
        <Loading />
        {:then weather}
              <WeatherData {weather}/>          
        {:catch err}
           <ErrorAlert {err}/>
        {/await}
    </div>
</div>

<style>
    .form-container{
        background-color: rgba(19, 65, 114, 0.091);
        padding: 20px;
        border-radius: 10px;
    }
    label{
        font-size: 20px;
        
    }

    button{
        margin-left: 5px;
        border-radius: 8px;
    }
</style>
