<script>
	let result = 0;

	let weightMetrics = '';
	let weightVal = 0;
	let heightVal = 0;
	let ageVal = 0;

	function CalculateCalories() {
		switch (weightMetrics) {
			case 'kg':
				result = 10 * weightVal + 6.25 * heightVal - 5 * ageVal;
				break;
			case 'lbs':
				result = 4.55 * weightVal + 6.25 * heightVal - 5 * ageVal;
				break;
		}
	}
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<div class="max-w-6xl mx-auto">
	<div>
		<section>
			<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
				<div class="flex flex-col lg:flex-row lg:items-center">
					<div
						class="mx-auto max-w-lg shrink-0 space-y-5 py-12 text-center lg:mx-0 lg:text-left xl:max-w-[620px]"
					>
						<h1
							id="convert-1-v3"
							class="text-3xl font-bold tracking-tight text-primary-500 sm:text-4xl sm:leading-[3rem] lg:text-[38px]"
						>
							Free Calorie Calculator
						</h1>
						<h2 class="text-xl font-semibold text-neutral-400 sm:text-xl">
							Get your base calories to start losing weight
						</h2>
						<p class="text-sm md:text-lg font-normal leading-[1.8rem] text-neutral-500">
							The Stupid Diet is very simple: Track your food, have a caloric deficit, observe the
							results and adjust accordingly.
						</p>
					</div>
				</div>
			</div>
		</section>
		<div class="relative">
			<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
				<section class="bg-neutral-800 rounded-lg border-2 border-neutral-700 py-12">
					<div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
						<div class="flex flex-col items-center justify-center gap-8 lg:gap-16">
							<h3 class="text-lg font-bold text-primary-500">Stupid Diet Calorie Calculator</h3>
							<form class="flex flex-col" on:submit={CalculateCalories}>
								<p>Weight</p>
								<div>
									<input
										type="number"
										placeholder="Weight"
										bind:value={weightVal}
										required
										class="p-2 rounded-lg bg-black"
									/>
									<select
										bind:value={weightMetrics}
										name="metric"
										id="metric"
										class="p-2 rounded-md bg-black"
									>
										<option value="kg">kg</option>
										<option value="lbs">lbs</option>
									</select>
								</div>

								<p>Height (cm)</p>
								<input
									type="number"
									placeholder="Height"
									bind:value={heightVal}
									required
									class="p-2 rounded-lg bg-black"
								/>

								Age
								<input
									type="number"
									placeholder="Age"
									bind:value={ageVal}
									required
									class="p-2 rounded-lg bg-black"
								/>

								<button
									type="submit"
									id="calculate-button"
									class="p-2 m-2 rounded-lg bg-black hover:bg-neutral-900"
								>
									Calculate
								</button>
							</form>
							{#if result > 0}
								<div>
									<h3 class="text-lg font-bold text-primary-500">Result</h3>
									<p>{result} Calories</p>
								</div>
							{/if}
						</div>
					</div>
				</section>
			</div>
		</div>
	</div>
</div>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
