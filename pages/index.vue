<template>
	<div class="container" style="padding: 80px 10px;display: flex">
		<v-row justify="center" align="top">
			<v-col cols="12" sm="6" md="4">
				<h3>
					IP Status
					<v-chip class="ma-2" :color="networkStatus.color" small>
						<v-icon small left>{{networkStatus.icon}}</v-icon>
						{{networkStatus.status}}
					</v-chip>
				</h3>
				<span class="text--disabled">{{latestUploaded}}</span>
				<v-card>
					<v-card-title>{{networkStatus.currentIP}}</v-card-title>
					<v-card-subtitle>Current IP</v-card-subtitle>
				</v-card>
				<br />
				<h3>Recording targets</h3>
				<span class="text--disabled">{{latestUploaded}}</span>
				<v-card>
					<v-simple-table>
						<template v-slot:default>
							<thead>
								<tr>
									<th class="text-left">Status</th>
									<th class="text-left">Channel</th>
								</tr>
							</thead>
							<tbody>
								<tr v-for="(item,i) in recordingTargets" :key="i">
									<td width="1.2em">{{ item.status }}</td>
									<td>{{ item.channel }}</td>
								</tr>
							</tbody>
						</template>
					</v-simple-table>
				</v-card>
			</v-col>
			<v-col cols="12" sm="6" md="8">
				<h3>Ongoing Records</h3>
				<span class="text--disabled">{{latestUploaded}}</span>
				<v-row justify="left" align="top">
					<v-col cols="6" sm="12" md="4" v-for="(item,i) in ongoingRecords" :key="i">
						<v-card>
							<v-img :aspect-ratio="16/9" :src="item.img"></v-img>
							<v-card-text>
								<h2 class="title primary--text">{{item.channel}}</h2>
								<span>{{item.title}}</span>
								<br />
								<span>{{item.time}}</span>
							</v-card-text>
						</v-card>
					</v-col>
				</v-row>
			</v-col>
			<v-col cols="12" sm="12" md="12">
				<h3>Recent uploads</h3>
				<span class="text--disabled">{{latestUploaded}}</span>
				<v-card>
					<v-simple-table fixed-header height="350px">
						<template v-slot:default>
							<thead>
								<tr>
									<th class="text-left">Channel</th>
									<th class="text-left">Title</th>
									<th class="text-left">SEG</th>
									<th class="text-left"></th>
								</tr>
							</thead>
							<tbody>
								<tr v-for="(item,i) in recentUploads" :key="i">
									<td>{{ item.channel }}</td>
									<td>{{ item.title }}</td>
									<td>{{ item.seg }}</td>
									<td width="1.2em">
										<v-btn icon :to="item.downloadLink">
											<v-icon small>mdi-download</v-icon>
										</v-btn>
									</td>
								</tr>
							</tbody>
						</template>
					</v-simple-table>
				</v-card>
			</v-col>
		</v-row>
	</div>
</template>

<script> 
export default {
	data: () => ({
		latestUploaded: "3 minutes ago",
		networkStatus: {
			currentIP: "1069:b1b1:1069:::87",
			status: "Functional",
			icon: "mdi-checkbox-marked-circle",
			color: "success",
		},
		recentUploads: [
			{
				channel: '勝勝',
				title: '我好可愛',
				seg: 'HAPPY-1234',
				downloadLink: '#',
			},
		],
		ongoingRecords: [
			{
				img: 'https://i.ytimg.com/vi/YN3ykwU3LTM/maxresdefault.jpg',
				channel: 'Gawr Gura',
				title: '勝勝太可愛了該怎麼辦',
				time: '1:06:09',
			},
			{
				img: 'https://i.ytimg.com/vi/YN3ykwU3LTM/maxresdefault.jpg',
				channel: 'Gawr Gura',
				title: '勝勝太可愛了該怎麼辦',
				time: '1:06:09',
			},
			{
				img: 'https://i.ytimg.com/vi/YN3ykwU3LTM/maxresdefault.jpg',
				channel: 'Gawr Gura',
				title: '勝勝太可愛了該怎麼辦',
				time: '1:06:09',
			},
		],
		recordingTargets: [
			{
				status: '❤️',
				channel: '勝勝',
			},
			{
				status: '🐧',
				channel: '豪可愛',
			},
		],
	})
}
</script>
