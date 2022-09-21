<template>
	<div class="payments-container">
		<div class="payments-header">
			<div class="wallet">
				<span class="account-credit">اعتبار حساب</span>
				<span class="amount">7,853,000</span>
				<span class="currency">تومان</span>
				<chipCard
					class="base-chip"
					background="#FFFFFF"
					color="#4461F2"
					title="افزایش اعتبار"
					iconRight="icon/blue-plus-icon.svg"
				/>
				<img src="@/assets/img/vectors/wallet-vector.svg" alt="error" />
			</div>
			<div class="transaction-cards">
				<transactionCard
					v-for="item in info"
					:image="item.image"
					:key="item.id"
					:title="item.title"
				/>
			</div>
		</div>
		<div class="table-container">
			<span>تاریخچه تراکنش های شما</span>
			<BaseTable
				:dataTable="dataTable"
				class="mt-1"
			/>
		</div>
	</div>
</template>

<script>
import chipCard from '@/components/elements/BaseChip/baseChip.vue';
import transactionCard from '../Wallet/transactionCard.vue';
import BaseTable from '@/components/elements/Table/BaseTable';
export default {
	data() {
		return {
			info: [
				{ title: 'برداشت از کیف', image: 'vectors/money-vector.svg' },
				{ title: 'انتقال کیف به کیف', image: 'vectors/transaction-vector.svg' },
			],
			dataTable: [
				{
					date: 'دوشنبه , 8 ,شهرویور',
					time: '21:30',
					paymentType: 'تست',
					paymentNumber: '321423143',
					price: '7,9999,000',
				},
				{
					date: 'دوشنبه , 8 ,شهرویور',
					time: '21:30',
					paymentType: 'تست',
					paymentNumber: '321423143',
					price: '7,9999,000',
				},
				{
					date: 'دوشنبه , 8 ,شهرویور',
					time: '21:30',
					paymentType: 'تست',
					paymentNumber: '321423143',
					price: '7,9999,000',
				},
				{
					date: 'دوشنبه , 8 ,شهرویور',
					time: '21:30',
					paymentType: 'تست',
					paymentNumber: '321423143',
					price: '7,9999,000',
				},
			],
		};
	},
	components: {
		chipCard,
		transactionCard,
		BaseTable,
	},
};
</script>

<style scoped lang="scss">
@import '@/assets/scss/_shared.scss';
.payments-container {
	margin-top: 80px;
	.table-container {
		display: flex;
		flex-direction: column;
		span {
			font-size: 23px;
			font-weight: 500;
		}
	}
}
.payments-header {
	display: flex;
	flex-direction: row;
}
.wallet {
	width: 657px;
	height: 230px;
	background: #fcbf00;
	box-shadow: 0px 12px 21px rgba(252, 191, 0, 0.15);
	border-radius: 15px;
	padding: 24px 24px;
	.account-credit {
		display: block;
		font-style: normal;
		font-weight: 400;
		font-size: 24px;
		line-height: 23px;
		color: #ffffff;
		margin-bottom: 32px;
	}
	.amount {
		font-style: normal;
		font-weight: 600;
		font-size: 40px;
		line-height: 20px;
		color: #ffffff;
	}
	.currency {
		font-style: normal;
		font-weight: 300;
		font-size: 17px;
		line-height: 20px;
		color: #ffffff;
		margin-right: 24px;
	}
	.base-chip {
		width: 185px;
		height: 48px;
		padding-top: 8px !important;
		margin: 30px 8px !important;
	}
	img {
		position: relative;
		right: 270px;
		top: -330px;
	}
}
.transaction-cards {
	display: flex;
	flex-direction: column;
}
</style>
