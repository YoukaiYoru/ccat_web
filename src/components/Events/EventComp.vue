<template>
			<v-card 
			class="ma-6 card-color">
				<v-row>
					<v-col cols="2">
						<v-img 
						:src= "eventImage"
						max-height="300px"
						width="300px"
						height="100%"
						cover
						></v-img>
					</v-col>
					<v-col>
					<v-card-text  class="h-auto">
							<h1 class="text-h3 font-weight-black color-title">{{title}} </h1>
							<p class="text-h5 text-start my-5 color-text"> {{ date }}</p>
							<p class="text-h5 text-start my-5 color-text"> {{ hour }}</p>
					</v-card-text>
					</v-col>
					<v-col cols="2" class="align-self-start">
						<v-card-actions>
						<v-btn block class="register-btn" @click="reveal= !reveal">Registro</v-btn>
						</v-card-actions>

						<v-chip-group>
							<v-chip 
							class="chip-color">
								{{ tag }}
							</v-chip>
						</v-chip-group>
					</v-col>
				</v-row>
				<v-expand-transition>
					<v-card v-if="reveal">
						<v-card-text>
							<p>AAAAA</p>
						</v-card-text>
					</v-card>
				</v-expand-transition>
			</v-card>

</template>

<style scoped>
.chip-color	{
	background-color: #D9E8F6;
}
.color-title{
	color:white ;
}
.color-text{
	color:#D9E8F6
}
.card-color{
	background-color:#778DA9 ;
}
.register-btn{
	background-color: #1B263B;
	color: white;
}
</style>

<script setup>
import { ref } from 'vue';
defineProps(['title','eventImage','date','hour','tag']);

const reveal=ref(false)

</script>