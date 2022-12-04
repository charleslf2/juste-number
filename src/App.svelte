<script>
	let max=20
	

	var user_input;
	var more=false
	var win=false

	var tenta= 10
	var tentative=10;
	var machine_number;

	const machine =(max)=>{
		machine_number=Math.floor(Math.random() * max)
		return machine_number
	}

	machine_number=machine(10)

	const Userpass =()=>{

		if (user_input< machine_number){
			more=true
			tentative=tentative-1
		}
		if (user_input> machine_number){
			more=false
			tentative=tentative-1
		}
		if (user_input == machine_number){
			win=true
			machine_number=machine(10)
		}
		
	}

	const othergame=()=>{
		win=false
		user_input=0
		tentative=tenta
	}


</script>


{#if win==true}
	<main>
		<p class="congrat">Congratulation you win</p>
		<button on:click={othergame}>another game </button>
	</main>
{/if}

{#if tentative==0}
	<main>
		<p class="lose">Sorry you lose </p>
		<button on:click={othergame}>Try again</button>
	</main>	
{/if}

{#if win==false}

	{#if more==true}
		<p style="color=red">It's more</p>
	{:else}
		<p style="color:red ;">It's less</p>
	{/if}
	<main>
		<h1 class="title">Juste Price</h1>
		<h3 class="machine_choose_print">machine choose a number between 0 and {max}</h3>
		
		<div class="message">

			<div class="message_ctn">


				{#if tentative >= 7 }
					<h3> Available Tentative <span class="tentatative" style="color:green;">{tentative}</span>  </h3>
				{:else if tentative <7 && tentative >=5}
				<h3> Available Tentative <span class="tentatative" style="color:yellow;">{tentative}</span>  </h3>
				{:else if tentative < 5}
				<h3> Available Tentative <span class="tentatative" style="color:red;">{tentative}</span>  </h3>
				{/if}
		

				<h3>settings</h3>
			</div>
			
		</div>
		


		<div class="user_field">
			<div class="user_content">
				<p class="label">Enter your price</p>
				<input class="input_field" type="number" min=0 max={max} bind:value={user_input} placeholder="enter your price" >
				<button class="button" on:click={Userpass}>Valid</button>
			</div>
			
		</div>


		<!-- <h1>{machine_number}</h1>
		<h3>user input = {user_input}</h3> -->
	</main>

{/if}



<style>

	main{
		/* border: 1px solid; */
		width: 100%;
		height: 100vh;
	}
	.title{
		/* border: 1px solid; */
		width: 100%;
		height: 10%;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 2.5rem;
	}

	.machine_choose_print{
		/* border: 1px solid; */
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 1rem;
	}

	.user_field{
		/* border: 1px solid; */
		width: 100%;
		margin-top: 1rem;
		display: flex;
		height: 55%;
		justify-content: center;
		align-items: center;
	}

	.user_content{
		/* border: 1px solid red; */
		background: #f0f8ff;
		border-radius: 2rem;
		width: 50%;
		display: flex;
		justify-content: center;
		flex-direction: column;
		height: 90%;
		align-items: center;
		gap: 2rem;
	}
	.label{
		/* border: 1px solid; */
		font-size: 2rem;
		
	}

	.input_field{
		border-radius: 1rem;
		background: none;
		width: 50%;
		height: 10%;
		white-space: 1rem;
	}

	.button{
		background: none;
		height: 10%;
		width: 30%;
		border-radius: 1rem;
		cursor: pointer;
		transition: all ease-in 300ms;
	}
	.button:hover{
		background-color:#00ffff ;
	}

	.message{
		/* border: 1px solid blue; */
		display: flex;
		justify-content: center;
		height: 7%;
		margin-top: 1rem;
		width: 100%;
	}

	.message_ctn{
		/* border: 1px solid; */
		height: 100%;
		width: 50%;
		display: flex;
		justify-content:center;
		align-items: center;
		gap: 2rem;
	}

	.congrat{
		width: 100%;
		background-color: green;
		display: flex;
		justify-content: center;
		height: 6vh;
		font-size: 2rem;
		color: white;
	
	}
	.lose{
		width: 100%;
		background-color: red;
		display: flex;
		justify-content: center;
		height: 6vh;
		font-size: 2rem;
		color: white;
	
	}
	
</style>