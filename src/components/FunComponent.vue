<template>
    <div>
        <button>Click me</button>
        <article>
            
        </article>
    </div>
</template>

<script>
    export default {
        name : "FunComponent",
        data() {
            return {
                isBlue: false,
                secrets : ["Fettuccine", 
                            "Watermelon", 
                            "Lasagna", 
                            "Taco",
                            "Donair Poutine", 
                            "Buddha Bowl",
                            "Pizza",
                            "Dates"
                        ]
            }
        },
        methods: {
            changeBackground() {
                if (this.isBlue){
                    document.body.style.backgroundColor = "white";
                    document.querySelector(`article`).style.color="black";

                } else{
                    document.body.style.backgroundColor = "blue";
                    document.querySelector(`article`).style.color="white";
                }
                this.isBlue = !this.isBlue;
            },
            changeText(event){
                let target = event.target;
                target.style.color = "pink";
            },
            addFoods(){
                for (let food of this.secrets){
                    document.querySelector('article').insertAdjacentHTML(`beforeend`,`<p>${food}</p>`)
                }
                let tags = document.querySelectorAll(`p`);
                for (let p of tags){
                    p.addEventListener(`click`, this.changeText);
                }
            }
        },
        mounted () {
            document.querySelector(`button`).addEventListener(`click`,this.changeBackground);
            this.addFoods();
        },
    }
</script>

<style scoped>

</style>