<template>
    <main class="main">
        <div class="main__items">
            <div class="main__search">
                <input type="search" class="main__input" id="searchInput" placeholder="Search for a country...">
                <button class="main__button" v-on:click="this.searchInfos()">Search</button>
            </div>
            <div class="main__dropdown">
                <select name="regions" id="region" class="main__select">
                    <option value="filter" class="main__option">Filter by Region</option>
                    <option value="africa" class="main__option" data-id="africa">Africa</option>
                    <option value="america" class="main__option" data-id="americas">Americas</option>
                    <option value="asia" class="main__option" data-id="asia">Asia</option>
                    <option value="europe" class="main__option" data-id="europe">Europe</option>
                    <option value="oceania" class="main__option" data-id="oceania">Oceania</option>
                    <option value="antartic" class="main__option" data-id="antartic">Antartic</option>
                </select>
            </div>
        </div>
        <div class="main__error" v-if="errored">
            Sorry, we couldn't find the informations. Please, try again later.
        </div>
        <div class="main__content" v-else>
            <h1 class="main__loading" v-if="loading">Loading...</h1>
            <div class="main__info" v-for="currency in info" :key="currency.id" v-else>
                <img class="main__image" :src="currency.flags.png" :alt="currency.name.common">
                <h1 class="main__title">{{ currency.name.common }}</h1>
                <p class="main__text">Population: {{ currency.population.toLocaleString('pt-BR') }}</p>
                <p class="main__text">Region: {{ currency.region }}</p>
                <p class="main__text">Capital: {{ String(currency.capital || 'Without Informations')}}</p> 
            </div>
        </div>  
    </main>
</template>

<script>
    export default {
        name: 'Main',
        data () {
            return {
                info: null,
                loading: true,
                errored: false,

                searchInfos() {
                    let input = document.getElementById('searchInput').value
                    input = input.toLowerCase()
                    let x = document.getElementsByClassName('main__info')
                    
                    for(let i = 0; i < x.length; i++) {
                        if (!x[i].innerHTML.toLowerCase().includes(input)) {
                            x[i].style.display = "none"
                        } else {
                            x[i].style.display = "block"
                        }
                    }
                },
                request() {
                    return axios
                    .get('https://restcountries.com/v3.1/all')
                    .then(response => (this.info = response.data)) 
                    .catch(error => {
                        console.log(error)
                        this.errored = true
                    })
                    .finally(() => this.loading = false)
                },
                filterOptions() {
                    const filterBtns = document.querySelectorAll('.main__option')

                    filterBtns.forEach(function(btn) {
                        btn.addEventListener('click', function(e) {
                            const category = e.currentTarget.dataset.id
                            const menuCountrys = menu.filter(function(MenuOptions) {
                                if (MenuOptions.category === category) {
                                    return MenuOptions
                                }
                            }) 
                        })
                    })
                }
            }
        },
        mounted() {
            this.request(),
            this.searchInfos(),
            this.filterOptions()
        }
    }
</script>

<style lang="scss">
    @import '../assets/variables.scss';

    .main {
        padding: 3rem;

        &__items {
            margin-bottom: 3rem;
            display: flex;
            justify-content: space-around;
        }

        &__input {
            padding: .7rem;
            background-color: $DarkBlue;
            border: none;
            border-radius: 5px;
            color: $White;

            &::placeholder {
                color: $White;
            }
        }

        &__button {
            background-color: $DarkBlue;
            color: $White;
            border: none;
            padding: .7rem;
            margin-left: 1rem;
            cursor: pointer;
            border-radius: 5px;
        }

        &__select {
            background-color: $DarkBlue;
            color: $White;
            padding: .8rem;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            width: 10rem;
        }
        
        &__error {
            color: $Red;
            font-size: 20px;
            font-weight: bold;
        }

        &__content {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 2rem;

            @include phone {
                grid-template-columns: repeat(1, 1fr);
            }

            @include tablet {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        &__loading {
            color: $White;
            font-size: 20px;
        }

        &__info {
            background-color: $DarkBlue;
            padding: 1rem;
            box-shadow: 0px 0px 10px 0px #000000;
        }

        &__image {
            max-width: 1000px;
            width: 100%;
            height: 50%;
        }

        &__title {
            font-weight: 800;
            font-size: 18px;
            line-height: 1.5;
        }

        &__title, &__text {
            color: $White;
            padding: .5rem;
        }

        &__text {
            font-size: 14px;
            font-weight: 600;
        }
    }

</style>