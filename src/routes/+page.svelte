<script lang="ts">
	import { onMount } from "svelte"
	import { slide, fly } from "svelte/transition"

	let videos = false
	let openLocations = false
	let openInfoSign = false
	let defaultMenu = true
	let recaps = false
	let OpenMenuBar = "w-0"
	let rotateChevron = ""
	let defaultMenuS = false


	let locations = [
		{
			images: ["candyland1.jpg", "candyland2.jpg", "candyland3.jpg", "candyland4.jpg"],
			name: "Candyland",
			description: "If your lookin to get some sweet lines in, heres where you'll do it",
			ageGroups: {
				Grom: "10am - 12pm",
				Pro: "12pm - 2pm",
				Legend: "2pm - 4pm"
			},
			location: 'Above <a class="express">Majestic</a> Lift, please take the <a class="express">Crest Express</a> and take the left path on the <a class="hardRun">Wintergreen</a> run.',
			showDetails: false,
			buttonOpen: "rotate-0",
		},
		{
			images: ["captainHook1.jpg", "captainHook2.jpg", "captainHook3.jpg", "captainHook4.jpg", "captainHook5.jpg"],
			name: "Captain Hook",
			description: "This is one of our more challenging runs, so keep your wits about you. If you decided to come to this spot, you're doing so at your own risk.",
			ageGroups: {
				Grom: "12am - 2pm",
				Pro: "2pm - 4pm",
				Legend: "10am - 12pm"
			},
			location: 'Right below the <a class="hardRun">Christy Bowl</a> path, take <a class="express">Milly Express</a> all the way up to the summit, and exit to the right. Take <a class="easiestRun">Main Street</a> all the way to Captain Hook.',
			showDetails: false,
			buttonRotation: "rotate-0"
		},
		{
			images: ["endlesswinter1.jpg", "endlesswinter2.webp", "endlesswinter3.jpg", "endlesswinter4.jpg", "endlesswinter5.jpeg"],
			name: "Endless Winter Channel",
			description: "This one will challenge your ability with multiple mega ramps, our signature S Rail, and for those unwilling, a smaller ramp with a moderate knuckle.",
			ageGroups: {
				Grom: "2pm - 4pm",
				Pro: "10am - 12pm",
				Legend: "12pm - 2pm"
			},
			location: 'For this run, you will take the <a class="express">Great Western Express</a> all the way up to the summit. You will then exit to your left and will see the Endless Winter Course right there.',
			showDetails: false,
			buttonRotation: "rotate-0"
		},
		{
			images: ["powderalley1.jpg", "powderalley2.jpg", "powderalley3.jpg", "powderalley4.jpg", "powderalley5.jpg"],
			name: "Powder Alley",
			description: "Want to test your speed? Well get ready for Powder Alley. We will line up six competitors at a time and see who can make it to the bottom first. Speed is the game.",
			ageGroups: {
				Grom: "8am - 10am",
				Pro: "4pm - 6pm",
				Legend: "6pm - 8pm"
			},
			location: 'Located to the left of <a class="express">Majestic Express</a>, you will take the <a class="express">Majestic Express</a> and pop out to the right. You will then shoot below <a class="express">Majestic Express</a> and make your way to the right.',
			showDetails: false,
			buttonRotation: "rotate-0"
		}
		
	]
	/*<a class="express"></a>  */
	/* <a class="hardRun"></a>  */
	/* <a class="easiestRun"></a>  */

	let elemCarousel: HTMLDivElement;

	// onMount(() => {
	// 	openingTransition = "translate-x-[0%]"
	// })

	// location modals
	

	function menuBar() {
		if (OpenMenuBar === "w-0") {
			OpenMenuBar = "w-10/12 md:w-6/12"
			rotateChevron = "rotate-180"
			defaultMenuS = true
		} else {
			defaultMenuS = false
			OpenMenuBar = "w-0"
			rotateChevron = ""
			
		}
	}
</script>

<!-- large screen component -->
<div class="hidden lg:flex justify-start w-full relative p-4 h-screen gap-4 bg-gray-100">
	<div class="flex basis-8/12">
		<img src="mountainMap.png" alt="map of brighton ski resort mountain" class="object-cover w-full rounded-lg shadow-lg "/>
	</div>

	<div class="basis-4/12 h-full border rounded-lg shadow-lg bg-gray-50 transition-all duration-300">

		<div class="h-1/6 bg-black flex w-full justify-center items-center rounded-t-lg">
			<div class="flex gap-12 py-4">
				<a href="https://brightonresort.com/" target="_blank"><img src="brighton_logo.png" class="h-14 w-14 spin" /></a>
				<a href="https://thebombhole.com/" target="_blank"><img src="bombhole_logo.png"  class="h-14 w-14 spinfast"/></a>
			</div>
		</div>

		{#if recaps}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {recaps = false; defaultMenu = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<p class="font-inter uppercase text-xl font-black px-4">Recaps</p>
				<p class=" mb-4 px-4">As we get into the spirit of the 3rd Annual Bomb Hole Cup, lets take a look at last years, recap!</p>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/_OaZh6xnUJk?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/7kOID4DMUtk?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/aoUOv1ysnV8?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<p class="mx-4 text-center">Checkout more videos at the Bomb Hole YouTube</p>
				<div class="my-4 mb-8 flex justify-center">
					<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
						<i class="fa-brands fa-youtube"></i>
						<a href="https://www.youtube.com/@TheBombHole" target="_blank" class=" text-xl font-inter uppercase font-black">The Bomb Hole</a>
					</div>
				</div>
			</div>
		{/if}

		{#if videos}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {videos = false; defaultMenu = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<p class="font-inter uppercase text-xl font-black px-4">Videos</p>
				<p class=" mb-4 px-4">Checkout some of the cool videos produced by the great Bomb Hole</p>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/GoRi7WkVuSU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/_2p_GHW-SXM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/ySL__2urR40" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<p class="mx-4 text-center">Checkout more videos at the Bomb Hole YouTube</p>
				<div class="my-4 mb-8 flex justify-center">
					<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
						<i class="fa-brands fa-youtube"></i>
						<a href="https://www.youtube.com/@TheBombHole" target="_blank" class=" text-xl font-inter uppercase font-black">The Bomb Hole</a>
					</div>
				</div>
			</div>
		{/if}

		<!-- information and signup section -->
		{#if openInfoSign}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {openInfoSign = false; defaultMenu = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<div class="mt-4">
					<div>
						<img src="milo.jpg" alt="">
					</div>
	
					<div class="p-4 justify-center">
						<p class="font-inter uppercase text-xl font-black">Competition Information</p>
						<p class="mb-4">Competition sign up will be start <a class="text-primary-red">April 1st</a>, at Milosport Skateshop and signup closes <a class="text-primary-red">April 30th</a> at 6pm MST</p>
						<a class="font-inter font-black uppercase ">Address:</a>
						<p>3119 E 3300 S</p>
						<p>Salt Lake City, UT</p>
						<p class="mb-4">84109</p>

						<a class="font-inter font-black uppercase ">Competition Categories:</a>
						<p>Grom Boys (age 14 and under)</p>
						<p>Grom Girls (age 14 and under)</p>
						<p>Pro Men (age 15 to 18)</p>
						<p>Pro Girls (age 15 to 18)</p>
						<p>Legend Men (age 18 and older)</p>
						<p>Legend Women (age 18 and older)</p>

						
						<p>For more information, please visit the Milosport's website</p>
						<div class="my-4 flex justify-center">
							<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
								<i class="fa-solid fa-globe"></i>
								<a href="https://www.milosport.com/" target="_blank" class=" text-xl font-inter uppercase font-black">Milosport</a>
							</div>
						</div>
					</div>
				</div>

			</div>
		{/if}
		
		<!-- default menu -->
		{#if defaultMenu}
			<div class="h-5/6">

				<div class="flex justify-center">
					<p class="font-inter uppercase text-xl font-black px-2 bg-black text-white my-4 rotate-32">The Bomb Hole Cup</p>
					<img src="trophy.png" class="h-14 w-14 rotate-[-16deg] translate-x-[-12px]"/>
				</div>

				<p class="px-4 pt-4"><a class="font-inter font-black uppercase ">Location:</a> Brighton Ski Resort</p>
				<p class="px-4 pt-2"><a class="font-inter font-black uppercase ">Date:</a> May 2nd, 2024</p>

				<div class=" flex w-full flex-wrap gap-4 p-4 ">
					<button out:fly={{x: 100, duration: 700}} on:click={() => {openLocations = true; defaultMenu = false}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-mountain-sun"></i>
						<p>View Locations</p>
					</button>

					<button on:click={() => {openInfoSign = true; defaultMenu = false}} out:fly={{x: 200, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-circle-info"></i>
						<p>Information & Signup</p>
					</button>

					<button on:click={() => {videos = true; defaultMenu = false}} out:fly={{x: 300, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-video"></i>
						<p>Videos</p>
					</button>

					<button on:click={() => {recaps = true; defaultMenu = false}} out:fly={{x: 400, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-video"></i>
						<p>Recaps</p>
					</button>
				</div>
			</div>
		{/if}

		<!-- menu for all the spots in the competition -->
		{#if openLocations}
			<div class="h-5/6 overflow-y-scroll flex flex-wrap p-4">

				<div class="basis-full w-full flex mb-4 items-center">
					<button on:click={() => {openLocations = false; defaultMenu = true}} class="flex ">
						<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300"></i>
					</button>
				</div>

				{#each locations as location (location.name)}
					<div class="bg-black p-4 rounded-lg shadow-lg mb-8">
						<div class="card grid grid-cols-[auto_1fr_auto] items-center">
							
							<!-- Full Images -->
							<div bind:this={elemCarousel} class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto rounded-t-md">
								{#each location.images as image}
									<img src={image} alt="location image" class="object-contain h-32 w-full shadow-lg "/>
								{/each}
							</div>
							
						</div>
						<h2 class="text-primary-yellow font-black font-inter uppercase my-2">{location.name}</h2>
						<p class="text-white"><a class=" font-inter font-bold">Location:</a> {@html location.location}</p>
						{#if location.showDetails}
							<div transition:slide >
								<p class="text-white my-8">{location.description}</p>
								<h3 class="text-primary-yellow font-black font-inter uppercase mb-1">Age Groups</h3>
								<ul class="text-white">
									{#each Object.keys(location.ageGroups) as ageGroup}
										<li class="text-white">{ageGroup}: {location.ageGroups[ageGroup]}</li>
									{/each}
								</ul>
							</div>
						{/if}
						<div class="w-full flex justify-center translate-y-8">
							<button on:click={() => {
								let updatedLocation = {...location, showDetails: !location.showDetails, buttonRotation: location.showDetails ? "rotate-0" : "rotate-180"};
								locations = locations.map(loc => loc.name === location.name ? updatedLocation : loc);
							}} class="fa-solid fa-chevron-down text-black hover:text-primary-yellow transition-all duration-300 {location.buttonRotation} py-2 px-2 bg-white rounded-full shadow-lg border border-gray-300 hover:bg-black"></button>
						</div>
						
					</div>
				{/each}
			</div>
		{/if}
	</div>
</div>


<!-- small screen component -->
<div class="bg-background lg:hidden flex justify-start w-full h-screen md:bg-gray-100 overflow-y-hidden">
	
	<img src="mountainMap2.png" alt="map of brighton ski resort mountain" class="object-cover w-full relative hidden md:block"/>

	<img src="mountainMap3.png" alt="map of brighton ski resort mountain" class="object-contain w-full relative md:hidden"/>
	
	<div class="absolute z-10 right-0 h-full bg-gray-50 rounded-t-lg {OpenMenuBar} transition-all duration-300">
		<div class="flex justify-center absolute z-10 top-6 left-[-3rem]">
			<button on:click={menuBar} class="fa-solid fa-chevron-left p-2 px-3 bg-black text-white rounded-full shadow-sm hover:text-primary-yellow shadow-primary-yellow {rotateChevron} transition-all duration-300"></button>
		</div>

		<div class="bg-black flex w-full justify-center items-center rounded-t-lg">
			<div class="flex gap-12 py-4">
				<a href="https://brightonresort.com/" target="_blank"><img src="brighton_logo.png" class="h-14 w-14 spin" /></a>
				<a href="https://thebombhole.com/" target="_blank"><img src="bombhole_logo.png"  class="h-14 w-14 spinfast"/></a>
			</div>
		</div>
	
		<!-- default menu -->
		{#if defaultMenuS}
			<div class="h-5/6">
	
				<div class="flex justify-center">
					<p class="font-inter uppercase text-xl font-black px-2 bg-black text-white my-4 rotate-32">The Bomb Hole Cup</p>
					<img src="trophy.png" class="h-14 w-14 rotate-[-16deg] translate-x-[-12px]"/>
				</div>
	
				<p class="px-4 pt-4"><a class="font-inter font-black uppercase ">Location:</a> Brighton Ski Resort</p>
				<p class="px-4 pt-2"><a class="font-inter font-black uppercase ">Date:</a> May 2nd, 2024</p>
	
				<div class=" flex w-full flex-wrap gap-4 p-4 ">
					<button out:fly={{x: 100, duration: 700}} on:click={() => {openLocations = true; defaultMenuS = false}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-mountain-sun"></i>
						<p>View Locations</p>
					</button>
	
					<button on:click={() => {openInfoSign = true; defaultMenuS = false}} out:fly={{x: 200, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-circle-info"></i>
						<p>Information & Signup</p>
					</button>
	
					<button on:click={() => {videos = true; defaultMenuS = false}} out:fly={{x: 300, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-video"></i>
						<p>Videos</p>
					</button>
	
					<button on:click={() => {recaps = true; defaultMenuS = false}} out:fly={{x: 400, duration: 700}} class="font-inter uppercase text-xl font-black border-2 py-2 border-black bg-black px-4 text-white shadow-md hover:shadow-lg hover:shadow-primary-yellow shadow-primary-yellow flex gap-2 items-center hover:translate-y-[-3px] transition-all duration-300">
						<i class="fa-solid fa-video"></i>
						<p>Recaps</p>
					</button>
				</div>
			</div>
		{/if}

		<!-- menu for all the spots in the competition -->
		{#if openLocations}
			<div class="h-5/6 overflow-y-scroll flex flex-wrap p-4">

				<div class="basis-full w-full flex mb-4 items-center">
					<button on:click={() => {openLocations = false; defaultMenuS = true}} class="flex ">
						<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300"></i>
					</button>
				</div>

				{#each locations as location (location.name)}
					<div class="bg-black p-4 rounded-lg shadow-lg mb-8">
						<div class="card grid grid-cols-[auto_1fr_auto] items-center">
							
							<!-- Full Images -->
							<div bind:this={elemCarousel} class="snap-x snap-mandatory scroll-smooth flex overflow-x-auto rounded-t-md">
								{#each location.images as image}
									<img src={image} alt="location image" class="object-contain h-32 w-full shadow-lg "/>
								{/each}
							</div>
							
						</div>
						<h2 class="text-primary-yellow font-black font-inter uppercase my-2">{location.name}</h2>
						<p class="text-white"><a class=" font-inter font-bold">Location:</a> {@html location.location}</p>
						{#if location.showDetails}
							<div transition:slide >
								<p class="text-white my-8">{location.description}</p>
								<h3 class="text-primary-yellow font-black font-inter uppercase mb-1">Age Groups</h3>
								<ul class="text-white">
									{#each Object.keys(location.ageGroups) as ageGroup}
										<li class="text-white">{ageGroup}: {location.ageGroups[ageGroup]}</li>
									{/each}
								</ul>
							</div>
						{/if}
						<div class="w-full flex justify-center translate-y-8">
							<button on:click={() => {
								let updatedLocation = {...location, showDetails: !location.showDetails, buttonRotation: location.showDetails ? "rotate-0" : "rotate-180"};
								locations = locations.map(loc => loc.name === location.name ? updatedLocation : loc);
							}} class="fa-solid fa-chevron-down text-black hover:text-primary-yellow transition-all duration-300 {location.buttonRotation} py-2 px-2 bg-white rounded-full shadow-lg border border-gray-300 hover:bg-black"></button>
						</div>
						
					</div>
				{/each}
			</div>
		{/if}


		<!-- information and signup section -->
		{#if openInfoSign}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {openInfoSign = false; defaultMenuS = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<div class="">
					<div>
						<img src="milo.jpg" alt="" class="w-full">
					</div>
	
					<div class="p-4 justify-center">
						<p class="font-inter uppercase text-xl font-black">Competition Information</p>
						<p class="mb-4">Competition sign up will be start <a class="text-primary-red">April 1st</a>, at Milosport Skateshop and signup closes <a class="text-primary-red">April 30th</a> at 6pm MST</p>
						<a class="font-inter font-black uppercase ">Address:</a>
						<p>3119 E 3300 S</p>
						<p>Salt Lake City, UT</p>
						<p class="mb-4">84109</p>

						<a class="font-inter font-black uppercase ">Competition Categories:</a>
						<p>Grom Boys (age 14 and under)</p>
						<p>Grom Girls (age 14 and under)</p>
						<p>Pro Men (age 15 to 18)</p>
						<p>Pro Girls (age 15 to 18)</p>
						<p>Legend Men (age 18 and older)</p>
						<p>Legend Women (age 18 and older)</p>

						
						<p>For more information, please visit the Milosport's website</p>
						<div class="mt-4 flex justify-center">
							<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
								<i class="fa-solid fa-globe"></i>
								<a href="https://www.milosport.com/" target="_blank" class=" text-xl font-inter uppercase font-black">Milosport</a>
							</div>
						</div>
					</div>
				</div>

			</div>
		{/if}

		{#if videos}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {videos = false; defaultMenuS = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<p class="font-inter uppercase text-xl font-black px-4">Videos</p>
				<p class=" mb-4 px-4">Checkout some of the cool videos produced by the great Bomb Hole</p>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/GoRi7WkVuSU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/_2p_GHW-SXM" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/ySL__2urR40" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<p class="mx-4 text-center">Checkout more videos at the Bomb Hole YouTube</p>
				<div class="my-4 mb-8 flex justify-center">
					<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
						<i class="fa-brands fa-youtube"></i>
						<a href="https://www.youtube.com/@TheBombHole" target="_blank" class=" text-xl font-inter uppercase font-black">The Bomb Hole</a>
					</div>
				</div>
			</div>
		{/if}


		{#if recaps}
			<div class="h-5/6 overflow-y-scroll">
				<button on:click={() => {recaps = false; defaultMenuS = true}} class="flex ">
					<i class="fa-solid fa-chevron-left p-2 px-3 border border-gray-300 rounded-full hover:bg-black hover:text-primary-yellow hover:shadow-md hover:shadow-primary-yellow hover:translate-y-[-3px] transition-all duration-300  m-4"></i>
				</button>

				<p class="font-inter uppercase text-xl font-black px-4">Recaps</p>
				<p class=" mb-4 px-4">As we get into the spirit of the 3rd Annual Bomb Hole Cup, lets take a look at last years, recap!</p>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/_OaZh6xnUJk?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/7kOID4DMUtk?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<iframe class="w-full h-3/6 mb-4" src="https://www.youtube.com/embed/aoUOv1ysnV8?list=PL0laC3SQpscDn-D-jI0BJgUMv2mWmoU_w" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

				<p class="mx-4 text-center">Checkout more videos at the Bomb Hole YouTube</p>
				<div class="my-4 mb-8 flex justify-center">
					<div class="flex bg-black text-white shadow-sm hover:shadow-lg shadow-primary-yellow hover:shadow-primary-yellow py-0 px-2 hover:translate-y-[-3px] transition-all duration-300 items-center gap-2">
						<i class="fa-brands fa-youtube"></i>
						<a href="https://www.youtube.com/@TheBombHole" target="_blank" class=" text-xl font-inter uppercase font-black">The Bomb Hole</a>
					</div>
				</div>
			</div>
		{/if}
	</div>
</div>

<style>
	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	.spin {
  		animation: spin 10s linear infinite;
	}

	@keyframes spinfast {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	.spinfast {
  		animation: spin 5s linear infinite;
	}
	:global(.express) {
		color: #AA2227;
	}
	:global(.hardRun) {
		color: #6f8cea;
	}
	:global(.easiestRun) {
		color: #38a84e;
	}
</style>