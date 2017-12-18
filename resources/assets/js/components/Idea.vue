<template>
    <div>
        <h2 class="text-center">Captura tus ideas</h2>
        <div class="well">
            <h4>En qué estás pensando?</h4>
            <form>
                <div class="input-group">
                    <input type="" class="form-control input-sm" maxlength="256">
                    <span class="input-group-btn">
                        <button type="submit" class="btn btn-primary btn-sm">
                            Agregar
                        </button>
                    </span>
                </div>
            </form>
            <hr>
            <ul class="list-unstyled">
                <li v-for="idea in ideas">
                    <p>
                        <small class="text-muted">
                            <em>{{ idea.created_at }}</em>
                        </small>
                        {{ idea.description }}
                    </p>
                </li>
            </ul>
        </div>      
    </div>
</template>

<script>
	import axios from 'axios'
    export default {
    	data(){
    		return {
    			ideas: [],
    		}
    	},

    	created: function () {
    		this.getIdeas();
    	},

    	methods:{
    		getIdeas: function () {
    			var urlIdeas = 'mis-ideas';
    			axios.get(urlIdeas).then(response=>{
    				this.ideas = response.data
    			});
    		}
    	}
    }
</script>
