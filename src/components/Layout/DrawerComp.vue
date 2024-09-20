<template>

	<!-- NAVBAR -->
	<v-app-bar  style="background-color: #778DA9" >

		<!-- button hamburguer -->
		<v-app-bar-nav-icon class="hamburger" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

		<!-- logo -->
		<v-card class="logo" elevation="0" flat color="transparent">
			<v-img
			:src="ccat_logo"
			height="48"
			width="48"
			></v-img>
		</v-card>

		<v-app-bar-title class="ccat-name">CCAT</v-app-bar-title>


		<!-- spacer -->
		<v-spacer></v-spacer>


		<v-card class="areas-buttons"  dark elevation="0">
			<!-- iterate over the list of buttons  -->
			<v-btn v-for="button in buttons"
			:key="button.id" class="nav-button"
			:href="button.path"
			>
				{{ button.title }}
			</v-btn>

			<v-menu
				open-on-hover
				>
				<template v-slot:activator="{ props }">
					<v-btn
						v-bind="props"
						class="nav-button"
					>
					Areas
					</v-btn>

				</template>

					<v-btn flat  v-for="(item, index) in items"
						:key="index"
					>
					{{ item.title }}
					</v-btn>
				</v-menu>

		</v-card>

	</v-app-bar>

	<!-- DRAWER-->
	<v-navigation-drawer  v-model="drawer"
	app fixed clipped temporary
	mini-variant
	expand-on-hover
	left>
		<v-list-item>
			<v-list-item-content>
				<v-list-item-title class="text-h6"> CCAT</v-list-item-title>
				<v-list-item-subtitle> ...más que un centro</v-list-item-subtitle>
			</v-list-item-content>
		</v-list-item>
		<v-divider></v-divider>
		<v-list dense nav>
			<v-list-item 
			v-for="button in buttons" 
			:key="button.id" 
			link
			:prepend-icon="button.icon"
			:title="button.title"
			:href="button.path"
			></v-list-item>
			<v-menu v-model="showlist"
			:close-on-content-click="false"
			transition="slide-x-transition"
			location="end"
			>

				<template v-slot:activator="{props}">
				<v-list-item
				@click="showlist = !showlist"
				:close-on-content-click="false"
				title="Áreas"
				prepend-icon="mdi-cog"
				v-bind:="props"
				>
				<template v-slot:append>
					<v-icon>{{ showlist ? 'mdi-chevron-left' : 'mdi-chevron-right' }}</v-icon>
				</template>
				</v-list-item>
				</template>
				<v-card>	
					<v-list
					v-for="item in items"
					:key="item"
					link
					class="pa-0 ma-o"
					>
						<v-btn class='nav-bar-xs'> {{ item.title }}</v-btn>
					</v-list>
				</v-card>


			</v-menu>

		</v-list>
	</v-navigation-drawer>

</template>

<script setup>

import {ref} from 'vue'
import ccat_logo from "@/assets/logo.png"
// // state of the drawer/buttons
const drawer = ref(false)

const showlist = ref(false)

const buttons = ref(
	[
		{id:1, title: 'Inicio', icon: 'mdi-home', path: '/' },
		// {id:2, title: 'Áreas', icon: 'mdi-account-box', path:'/areas' },
		{id:2, title: 'Proyectos', icon: 'mdi-cog', path:'/projects' },
		{id:3, title: 'Eventos', icon: 'mdi-cog', path:'/events' },
	]
)

const items = ref([
	{id: 1, title: 'IDI'},
	{id: 2, title: 'Academica'},
	{id: 3, title: 'GTH'},
	{id: 4, title: 'Logistica'},
])



</script>

<style scoped>
.nav-bar-xs{
	width: 100%;
	margin: auto;
	border-radius: 0px;
}
.navbar{
	/* background-color: #D9E8F6; */
	background-color: #778DA9;
}

/* align text of the name to the left  */
.ccat-name{
	text-align: left;
	/* make it bold */
	font-weight: bold;
	/* make it white*/
	color: #778DA9;
}

/* add a margin to the buttons container */
.areas-buttons{
	margin-right: 20px;
	background-color: #778DA9;
	/* align the text in the middle of the container */
	align-items: center;

}

/* hide the hamburger menu */
.hamburger{
	display: none;
}

/* font size of nav-button is bigger */
.nav-button{
	text-align: center;
	font-size: 1.3rem;
	min-width: 200px;
	max-width: 300px;
	font-family: 'Roboto', sans-serif;
	color: #01225E;
	/* text in lowercase */
	text-transform: none;
	/* align text in the center from top to bottom  */
	align-items: center;
	height: 40px;
}

/* the logo has a left margin of 10 px */
.logo{
	margin-left: 40px;
}

/* when reaching mobile dimensions hide .areas-buttons and show the hamburger menu */
@media (max-width: 915px) {
	.areas-buttons{
		display: none;
	}
	.hamburger{
		display: block;
	}
	.logo{
		margin-left: 0px;
	}
}
</style>
