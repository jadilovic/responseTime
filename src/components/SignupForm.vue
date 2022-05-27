<template>
	<form @submit.prevent="handleSubmit">
		<label>Email:</label>
		<input type="email" required v-model="email" />
		<label>Password:</label>
		<input type="password" required v-model="password" />
		<div v-if="passwordError" class="error">{{ passwordError }}</div>
		<label for="">Role: </label>
		<select name="" id="" v-model="role">
			<option value="developer">Web Developer</option>
			<option value="designer">Web Designer</option>
		</select>
		<input type="checkbox" required v-model="terms" />
		<label for="">Accept terms and conditions</label>
		<div>
			<input type="checkbox" value="mario" v-model="names" />
			<label for="">Mario</label>
			<input type="checkbox" value="stanio" v-model="names" />
			<label for="">Stanio</label>
			<input type="checkbox" value="olio" v-model="names" />
			<label for="">Olio</label>
		</div>
		<div>
			<label for="">Skills:</label>
			<input type="text" v-model="tempSkill" @keyup="handleKey" />
			<div v-for="skill in skills" :key="skill" class="pill">
				<span @click="deleteSkill"> {{ skill }}</span>
			</div>
		</div>
		<div class="submit">
			<button>Submit</button>
		</div>
	</form>
	<p>Email: {{ email }}</p>
	<p>Password: {{ password }}</p>
	<p>Role: {{ role }}</p>
	<p>Terms: {{ terms }}</p>
	<p>Names: {{ names }}</p>
	<p>Skills: {{ tempSkill }}</p>
</template>

<script>
export default {
	data() {
		return {
			email: 'bobo',
			password: '',
			role: 'designer',
			terms: false,
			names: [],
			tempSkill: '',
			skills: [],
			passwordError: '',
		};
	},
	methods: {
		handleKey(e) {
			if (e.key === ',' && this.tempSkill) {
				if (!this.skills.includes(this.tempSkill)) {
					this.skills.push(this.tempSkill);
				}
				this.tempSkill = '';
			}
		},
		deleteSkill(e) {
			console.log(e.target.outerText);
			const index = this.skills.indexOf(e.target.outerText);
			if (index > -1) {
				this.skills.splice(index, 1);
			}
		},
		handleSubmit() {
			this.passwordError =
				this.password.length > 5
					? ''
					: 'Password must be minimum 5 characters long';

			if (!this.passwordError) {
				console.log('Email : ', this.email);
				console.log('Password : ', this.password);
				console.log('Role : ', this.role);
				console.log('Names : ', this.names);
				console.log('Skills : ', this.skills);
			}
		},
	},
};
</script>

<style>
form {
	max-width: 420px;
	margin: 30px auto;
	background: green;
	text-align: left;
	padding: 40px;
	border-radius: 10px;
}
label {
	color: #aaa;
	display: inline-block;
	margin: 25px 0 15px;
	font-size: 0.6em;
	text-transform: uppercase;
	letter-spacing: 1px;
	font-weight: bold;
}

input,
select {
	display: block;
	padding: 10px 6px;
	width: 100%;
	box-sizing: border-box;
	border: none;
	border-bottom: 1px solid #ddd;
	color: #555;
	border-radius: 5px;
}
input[type='checkbox'] {
	display: inline-block;
	width: 16px;
	margin: 0, 10px, 0, 0;
	position: relative;
	top: 2px;
}
.pill {
	display: inline-block;
	margin: 20px 10px 0 0;
	padding: 6px 12px;
	background: #eee;
	border-radius: 20px;
	font-size: 12px;
	letter-spacing: 1px;
	font-weight: bold;
	color: #777;
	cursor: pointer;
}
button {
	background: blue;
	border: 0;
	padding: 10px 20px;
	margin-top: 20px;
	color: white;
	border-radius: 20px;
	cursor: pointer;
}
.submit {
	text-align: center;
}
.error {
	color: red;
	margin-top: 10px;
	font-size: 0.8em;
	font-weight: bold;
}
</style>
