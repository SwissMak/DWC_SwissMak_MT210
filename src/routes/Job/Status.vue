<style scoped>
.chart-height-limit {
	max-height: 320px;
}
</style>

<template>
	<div class="d-flex flex-column pt-2" v-if="SettingMode">
		<job-progress></job-progress>

		<v-row>
			<v-col order="1" order-md="1" cols="12" sm="6" md="3" xl="2" class="py-0">
				<v-row align="center">
					<v-col cols="12">
						<job-control-panel></job-control-panel>
					</v-col>
					<v-col cols="12">
						<!-- <z-babystep-panel></z-babystep-panel> -->
					</v-col>
					<v-col class="hidden-sm-and-down">
						<!-- <job-info-panel></job-info-panel> -->
					</v-col>
					<v-col cols="12" class="d-none d-sm-block d-md-none">
						<!-- <speed-factor-panel></speed-factor-panel> -->
					</v-col>
					<v-col cols="12" class="d-none d-sm-block d-md-none">
						<!-- <extrusion-factors-panel></extrusion-factors-panel> -->
					</v-col>
				</v-row>
			</v-col>

			<v-col order="0" order-md="2" cols="12" md="5" xl="7" class="py-0 d-none d-sm-flex flex-column">
				<v-row>
					<v-col
					@click="isCooling = !isCooling"
					cols="3">
						<code-btn
						height="100"
						:color="isCooling ? 'warning' : 'primary'"
						:code="isCooling ? 'M106 P4 S0' : 'M106 P4 S255'"
						block 						
						tabindex="0">
							<v-icon class="mr-1">{{ isCooling ? 'mdi-stop' : 'mdi-play' }}</v-icon> Cooling
						</code-btn>
					</v-col>
					<v-col cols="3">
						
					</v-col>
					<v-col cols="3">
						
					</v-col>
					<v-col cols="3">
						
					</v-col>
					
				</v-row>
				<!-- <layer-chart class="chart-height-limit" :class="{ 'my-3': $vuetify.breakpoint.mdAndUp }"></layer-chart>
:code="isCooling ? 'M106 P4 S0' : 'M106 P4 S255'"
				<v-row class="flex-grow-0 flex-shrink-1 d-none d-md-flex">
					<v-col cols="12">
						<job-estimations-panel></job-estimations-panel>
					</v-col>
					<v-col cols="12">
						<job-data-panel></job-data-panel>
					</v-col>
				</v-row>

				<v-row class="flex-grow-0 flex-shrink-1 hidden-sm-and-up mt-3">
					<v-col cols="6" md="6">
						<fans-panel></fans-panel>
					</v-col>
					<v-col cols="6" md="6">
						<speed-factor-panel></speed-factor-panel>
					</v-col>
				</v-row> -->
			</v-col>

			<v-col order="2" order-md="3" cols="12" sm="6" md="4" xl="3" class="py-0">
				<v-row>
					<v-col cols="12" class="hidden-md-and-up">
						<job-estimations-panel></job-estimations-panel>
					</v-col>
					<v-col cols="12" class="hidden-md-and-up">
						<job-data-panel></job-data-panel>
					</v-col>
					<v-col cols="12" class="hidden-md-and-up">
						<job-info-panel></job-info-panel>
					</v-col>

					<v-col cols="12" class="hidden-sm-only">
						<speed-factor-panel></speed-factor-panel>
					</v-col>
					<!-- <v-col cols="12">
						<fans-panel></fans-panel>
					</v-col> -->
					<!-- <v-col cols="12" class="hidden-sm-only">
						<extrusion-factors-panel></extrusion-factors-panel>
					</v-col> -->
				</v-row>
			</v-col>
		</v-row>
	</div>
</template>


<script>
'use strict'
import { mapState } from 'vuex'
export default {
	computed: {
		...mapState('machine/model', {
			fans: state => state.fans,
		}),
		SettingMode(){
            return (this.fans[13] != undefined) && this.fans[13].actualValue;
        },
    },
	data() {
		return {			
			isCooling : false,
		}
	},
	methods: {
		getLog(_value){
			console.log(_value);
		},
	},

}
</script>
