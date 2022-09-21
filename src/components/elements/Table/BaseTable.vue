<template>
	<div class="base-table">
		<table class="table">
			<thead>
				<tr>
					<th class="title" scope="col">تاریخ</th>
					<th class="title" scope="col">ساعت</th>
					<th class="title" scope="col">نوع تراکنش</th>
					<th class="title" scope="col">شماره تراکنش</th>
					<th class="title" scope="col">مبلغ</th>
				</tr>
			</thead>
			<tbody v-for="data in dataTable" :key="data.id">
				<tr>
					<th>{{ data.date }}</th>
					<td>{{ data.time }}</td>
					<td>{{ data.paymentType }}</td>
					<td>{{ data.paymentNumber }}</td>
					<td>{{ data.price }}</td>
				</tr>
			</tbody>
		</table>
	</div>
</template>

<script>
export default {
	props: {
		dataTable: {
			type: Array,
			required: true,
		},
	},
};
</script>

<style scoped lang="scss">
.title {
    font-size: 18px;
    font-weight: 600;
}
</style>
