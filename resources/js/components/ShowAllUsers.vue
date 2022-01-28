<template>
    <div class="container mt-2">
        <div class="row justify-content-center">
            <div class="col-md-8 w-100">
                <div class="card">
                    <div class="card-header">List of Users</div>
                    <div class="card-body">
                        <div class="panel panel-default">
                            <div class="panel-body">
                                <table class="table">
                                    <thead>
                                    <tr>
                                        <th>ID</th>
                                        <th>Name</th>
                                        <th>Email</th>
                                    </tr>
                                    </thead>
                                    <tbody>
                                    <tr v-for="user in users">
                                        <td>{{ user.id }}</td>
                                        <td>{{ user.name }}</td>
                                        <td>{{ user.email }}</td>
                                    </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {

    data: function () {
        return {
            users: []
        }
    },

    methods: {
        getUsers() {
            axios.get('/users')
                .then((response) => this.users = response.data)
                .catch((error) => console.log(error.message))
        }
    },

    created() {
        this.getUsers();
    },
}
</script>
