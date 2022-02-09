<template>
    <div class="quote">
        <p>{{quote}}</p>
        <p>~ {{author}}</p>
    </div>
</template>

<script>
export default {
    name: 'Quotes',
    data() {
        return {
            quote: '',
            author: '',
        }
    },
    methods: {
        async newQuote(){
            fetch("https://quotes15.p.rapidapi.com/quotes/random/?language_code=en", {
	"method": "GET",
	"headers": {
		"x-rapidapi-host": "quotes15.p.rapidapi.com",
		"x-rapidapi-key": "e33e7e2ed0msh892b2efa6865100p1017fcjsn1fc34ba00b5c"
	}
})
.then(response => response.json())
.then(response => {
    this.quote = response.content
    this.author = response.originator.name
})
.catch(err => {
	console.error(err);
});
        }
    },
    mounted () {
  this.newQuote()
        }
}
</script>