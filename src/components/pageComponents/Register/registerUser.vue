<template>
	<div class="register">
		<div class="container-fluid">
			<div class="login-user">
				<div class="container">
					<div class="row">
						<div class="col-lg-6">
							<img class="mt-3" src="@/assets/vectors/Contemo-Logo.svg" />
						</div>
						<div class="col-lg-6 d-flex app-ltr">
							<div class="mt-4">
								<router-link class="mt-4 px-4 login-router" to="/login"
									>ورود</router-link
								>
							</div>
							<div class="mt-4">
								<router-link class="mt-4 register-router" to="/register"
									>ثبت نام</router-link
								>
							</div>
						</div>
					</div>
				</div>
			</div>
			<div class="row form-base-container">
				<div class="col-lg-8 d-flex w-50">
					<div class="flex-column align-items-center mt-5 d-flex justify-content-center">
						<h1 class="" style="padding-right: 120px">به کانتمو خوش آمدید</h1>
						<h5 style="padding-right: 120px">
							اگر قبلا ثبت نام کردی میتونی از
							<router-link to="/login">اینجا</router-link> وارد حسابت بشی
						</h5>
					</div>
					<div class="col-lg-6">
						<img
							class="register_image mt-5"
							src="@/assets/vectors/register-vector.svg"
							alt=""
						/>
					</div>
				</div>
				<div class="col-lg-4 mt-5">
					<validation-observer v-slot="{ valid }">
						<form class="app" @submit.prevent="registerUser">
							<div class="form-group">
								<validation-provider
									name="آدرس ایمیل"
									rules="required|email"
									:bails="false"
									v-slot="{ errors }"
								>
									<BaseInput
										ref="email"
										type="email"
										name="email"
										v-model="model.email"
										:errors="errors"
										placeholder="آدرس ایمیل"
										icon="icon/envelope-icon.svg"
									/>
								</validation-provider>
							</div>
							<div class="form-group">
								<validation-provider
									name="شماره تلفن"
									rules="required|length:11"
									:bails="false"
									v-slot="{ errors }"
									ref="phoneNumber"
									type="phoneNumber"
								>
									<BaseInput
										v-model="model.phoneNumber"
										placeholder="شماره تلفن"
										:errors="errors"
									/>
								</validation-provider>
							</div>
							<div class="form-group">
								<validation-provider
									name="رمز عبور"
									rules="required"
									:bails="false"
									v-slot="{ errors }"
								>
									<BaseInput
										ref="password"
										type="password"
										name="password"
										v-model="model.password"
										placeholder="رمز عبور"
										:errors="errors"
										icon="icon/lock-icon.svg"
									/>
								</validation-provider>
							</div>
							<div class="form-group">
								<validation-provider
									name="تکرار رمز عبور"
									rules="required"
									:bails="false"
									v-slot="{ errors }"
								>
									<BaseInput
										ref="password"
										type="password"
										name="password"
										v-model="model.confrimPassword"
										placeholder="تکرار رمز عبور"
										:errors="errors"
										icon="icon/lock-icon.svg"
									/>
								</validation-provider>
							</div>
							<!-- <div class="form-group">
									<BaseInput
										v-model="model.marketingCode"
										placeholder="کد بازاریابی"
									/>
								</div> -->
							<BaseButton
								title="ثبت نام"
								class="mt-3"
								:disabled="!valid"
								@click.native="registerUser"
							/>

							<div class="hr-sect mt-3">با این حساب وارد شو</div>
							<div class="row mt-2">
								<div class="col-md-4">
									<button class="btn btn-social btn-light">
										<img src="@/assets/vectors/Facebook.svg" alt="" />
									</button>
								</div>
								<div class="col-md-4">
									<button class="btn btn-social btn-light">
										<img src="@/assets/vectors/linkedin.svg" alt="" />
									</button>
								</div>
								<div class="col-md-4">
									<button class="btn btn-social btn-light">
										<img src="@/assets/vectors/googleIcon.svg" alt="" />
									</button>
								</div>
							</div>
						</form>
					</validation-observer>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import BaseInput from '@/components/elements/BaseInput/index.vue';
import BaseButton from '@/components/elements/Button/Button.vue';
export default {
	data() {
		return {
			model: {
				email: '',
				phoneNumber: '',
				password: '',
				confrimPassword: '',
				// marketingCode: '',
			},
		};
	},
	components: {
		BaseInput,
		BaseButton,
	},
	methods: {
		async registerUser() {
			const res = await this.$ApiServiceLayer.post(this.$PATH.RELATIVE_PATH.POST.REGISTER, {
				email: this.model.email,
				phone: this.model.phoneNumber,
				password: this.model.password,
				confirm: this.model.confrimPassword,
				// marketingCode: this.model.marketingCode,
			});
			console.log(res);
		},
	},
};
</script>
<style scoped lang="scss">
@import '@/assets/scss/_shared.scss';
.register {
	width: 100%;
	height: 100vh;
	background: $color-white;
}
.color-primary {
	background-color: $color-primary;
}
.input-form {
	box-shadow: -2px 4px 10px 0px rgba(0, 0, 0, 0.05);
	border: none;
	border-radius: 10px;
}
.input-form:active {
	box-shadow: -2px 4px 10px 0px rgba(0, 0, 0, 0.05);
	border: 1px solid #fcbf00;
	border-radius: 10px;
}
.border_primary:active {
	border: 1px solid $color-warning;
}

.register_image {
	width: 500px;
	margin-top: -10%;
}
.login-router {
	color: $color-secoundary;
	font-weight: 500;
	font-size: 15px;
}
.register-router {
	background: #fafafa;
	padding: 10px 50px;
	border-radius: 21px;
	box-shadow: rgba(0, 0, 0, 0.05);
	font-weight: 700;
	font-size: 17px;
}
.hr-sect {
	display: flex;
	flex-basis: 100%;
	align-items: center;
	color: $color-secoundary;
	margin: 8px 0px;
	font-size: 1rem;
}
.input_form {
	box-shadow: -2px 4px 10px 0px rgba(0, 0, 0, 0.05);
	border: none;
	border-radius: 10px;
}
.hr-sect::before,
.hr-sect::after {
	content: '';
	flex-grow: 1;
	background: $color-secoundary;
	height: 1px;
	font-size: 0px;
	line-height: 0px;
	margin: 0px 8px;
}
.btn-social {
	background: #f6f6f6;
	border: 1px solid #dddfdd;
	border-radius: 10px;
	width: 100%;
}
.form-base-container {
	width: 100%;
	height: 80vh;
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>
