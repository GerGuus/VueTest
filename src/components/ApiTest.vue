<template>
  <div class="root">
    <h1>Posts</h1>
    <table>
      <thead>
      <tr>
        <th>User Id</th>
        <th>ID</th>
        <th>Title</th>
        <th>Body</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="post in posts.slice(0, 10)" :key="post.id">
        <td>{{ post.userId }}</td>
        <td>{{ post.id }}</td>
        <td>{{ post.title }}</td>
        <td>{{ post.body }}</td>
      </tr>
      </tbody>
    </table>

    <h1>Users</h1>
    <table>
      <thead>
      <tr>
        <th>Id</th>
        <th>Name</th>
        <th>UserName</th>
        <th>Email</th>
        <th>Address</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="user in users.slice(0, 10)" :key="user.id">
        <td>{{ user.id }}</td>
        <td>{{ user.name }}</td>
        <td>{{ user.username }}</td>
        <td>{{ user.email }}</td>
        <td>{{ user.address }}</td>
      </tr>
      </tbody>
    </table>

    <h1>Users posts where userId=1</h1>
    <table>
      <thead>
      <tr>
        <th>User Id</th>
        <th>ID</th>
        <th>Title</th>
        <th>Body</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="post in usersPosts.slice(0, 10)" :key="post.id">
        <td>{{ post.userId }}</td>
        <td>{{ post.id }}</td>
        <td>{{ post.title }}</td>
        <td>{{ post.body }}</td>
      </tr>
      </tbody>
    </table>

    <h1>Comments of 1st post</h1>
    <table>
      <thead>
      <tr>
        <th>Post Id</th>
        <th>Id</th>
        <th>Name</th>
        <th>Body</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="comment in post" :key="comment.id">
        <td>{{ comment.postId }}</td>
        <td>{{ comment.id }}</td>
        <td>{{ comment.name }}</td>
        <td>{{ comment.body }}</td>
      </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
export default {
  name: 'ApiTest',
  created() {
    fetch('https://jsonplaceholder.typicode.com/posts')
        .then(response => response.json())
        .then(json => this.posts = json)
    fetch('https://jsonplaceholder.typicode.com/users')
        .then(response => response.json())
        .then(json => this.users = json)
    fetch('https://jsonplaceholder.typicode.com/posts?userId=1')
        .then(response => response.json())
        .then(json => this.usersPosts = json)
    fetch('https://jsonplaceholder.typicode.com/posts/1/comments')
        .then(response => response.json())
        .then(json => this.post = json)
  },
  data(){
    return {
      posts: '',
      users: '',
      usersPosts: '',
      post: '',
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
