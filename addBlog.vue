<template>
    <div id="add-blog">
        <h2>Add a New Blog</h2>
        <form v-if="!submitted">
            <div class="date">
                <label>Date:</label>
                <input type="text" v-model.lazy="blog.date" placeholder="Enter today's date" required/>
            </div>
            
            
            <div id="checkboxes">
                <p>Categories:</p>
                <label>Science</label>
                <input type="checkbox" value="Science" v-model="blog.categories" />
                <label>Medicine</label>
                <input type="checkbox" value="Medicine" v-model="blog.categories" />
                <label>Politics</label>
                <input type="checkbox" value="Politics" v-model="blog.categories" />
                <label>Technology</label>
                <input type="checkbox" value="Technology" v-model="blog.categories" />
                <label>Fashion</label>
                <input type="checkbox" value="Fashion" v-model="blog.categories" />
                <label>Business</label>
                <input type="checkbox" value="Business" v-model="blog.categories" />
                <label>Studies</label>
                <input type="checkbox" value="Studies" v-model="blog.categories" />
                <label>Commercials</label>
                <input type="checkbox" value="Commercials" v-model="blog.categories" />
                <label>International</label>
                <input type="checkbox" value="International" v-model="blog.categories" />
                <label>National</label>
                <input type="checkbox" value="National" v-model="blog.categories" />
                <label>Entertainment</label>
                <input type="checkbox" value="Entertaiment" v-model="blog.categories" />
                <label>Literature</label>
                <input type="checkbox" value="Literature" v-model="blog.categories" />
                <label>Research</label>
                <input type="checkbox" value="Research" v-model="blog.categories" />
                 <label>Market</label>
                <input type="checkbox" value="Market" v-model="blog.categories" />
                 <label>Current Affairs</label>
                <input type="checkbox" value="CurrentAffairs" v-model="blog.categories" />
                 <label>Suggestion</label>
                <input type="checkbox" value="Suggetsion" v-model="blog.categories" />
                 <label>Gaming</label>
                <input type="checkbox" value="Gaming" v-model="blog.categories" />
                <label>Others</label>
                <input type="checkbox" value="Interesting" v-model="blog.categories" />
            </div>
            <label>Title:</label>
            <input type="text" placeholder="Enter your blog's title" v-model.lazy="blog.title" required />
            <label>Content:</label>
            <textarea placeholder="Give your contents here !" v-model.lazy.trim="blog.content"></textarea>
            <label>Author:</label>
            <input type="text" placeholder="name" v-model.lazy="blog.author" required />
            <label>Contact Details:</label>
            <input type="text" placeholder="enter your e-mail" v-model.lazy="blog.email" required/>
            
            
        </form>
          <p v-if="errors.length">
         <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors">{{ error }}</li>
    </ul>
  </p>
        <div v-if="submitted">
            <h3>Thanks for adding your post</h3>
        </div>
        <div id="preview">
            <h3>Preview :)</h3>
            <p>Date: {{blog.date}}</p>
            <p>Categories:</p>
            <ul>
                <li v-for="category in blog.categories">{{ category }}</li>
            </ul>
            <p>Title: {{ blog.title }}</p>
            <p>Content:</p>
            <p>{{ blog.content }}</p>
            
            
            <p>Author: {{ blog.author }}</p>
            <p>Contact Details: {{blog.email}}</p>
            
        </div>
        <button v-on:click.prevent="post">Add Blog</button>
    </div>
</template>

<script>

export default {
    data () {
        return {
            blog: {
                error:[],
                title: '',
                content: '',
                categories: [],
                author: '',
                email:''
            },
           
            submitted: false
        }
    },
    methods: {
         checkForm: function (a) {
      if (this.content && this.title) {
        return true;
      }

      this.errors = [];

      if (!this.content) {
        this.errors.push('content required.');
      }
      if (!this.title) {
        this.errors.push('title required.');
      }

      a.preventDefault();
    },
        post: function(){
            this.$http.post('https://blogsite-2411.firebaseio.com/posts.json',this.blog ).then(function(data){
                console.log(data);
                this.submitted = true;
            });
        }
    }
}
</script>
<style scoped>

#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 30px;
    width: 150px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 60px;
    font-size: 50px;
    text-align: center;
}

#add-blog label{
    font-size: 30px;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
#add-blog button{
    margin-top: 25px;
    height: 30px;
    width: 100px;
    background: #000;
    color: white;
    
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview h3{
    font-size: 40px;
}
#preview p{
    font-size:20px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #000;
    margin: 30px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes p{
    font-size: 30px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 23px;
}

@media(min-width: 300px){

#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 6px;
    width: 140px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 12px;
    font-size: 40px;
    text-align: center;
    color: rgb(0, 0, 0);
}

#add-blog label{
    font-size: 20px;
}
#add-blog{
    margin: 5px auto;
    max-width: 250px;
}
#add-blog button{
    margin-top: 25px;
    height: 30px;
    width: 80px;
    background: #000;
    color: white;
    
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 5px;
}
#preview h3{
    font-size: 25px;
}
#preview p{
    font-size:15px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #000;
    margin: 30px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes p{
    font-size: 25px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 15px;
}

}
@media(min-width: 500px){
 
#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 30px;
    width: 180px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 12px;
    font-size: 40px;
    text-align: center;
    color: rgb(0, 0, 0);
}

#add-blog label{
    font-size: 25px;
}
#add-blog{
    margin: 5px auto;
    max-width: 400px;
}
#add-blog button{
    margin-top: 25px;
    height: 35px;
    width: 85px;
    background: #000;
    color: white;
    
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 6px;
}
#preview h3{
    font-size: 30px;
}
#preview p{
    font-size:20px;
}
#preview{
    padding: 15px 25px;
    border: 1px dotted #000;
    margin: 35px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 10px;
}
#checkboxes p{
    font-size: 25px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 15px;
}

}
@media(min-width: 700px){
#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 35px;
    width: 210px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 20px;
    font-size: 50px;
    text-align: center;
    color: rgb(0, 0, 0);
}

#add-blog label{
    font-size: 35px;
}
#add-blog{
    margin: 5px auto;
    max-width: 600px;
}
#add-blog button{
    margin-top: 25px;
    height: 40px;
    width: 90px;
    background: #000;
    color: white;
    
}
label{
    display: block;
    margin: 25px 0 15px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview h3{
    font-size: 35px;
}
#preview p{
    font-size:25px;
}
#preview{
    padding: 15px 25px;
    border: 1px dotted #000;
    margin: 35px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 0px;
}
#checkboxes p{
    font-size: 35px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 23px;
}

}
@media(min-width: 1000px){
#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 35px;
    width: 210px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 20px;
    font-size: 65px;
    text-align: center;
    color: rgb(0, 0, 0);
}

#add-blog label{
    font-size: 40px;
}
#add-blog{
    margin: 5px auto;
    max-width: 900px;
}
#add-blog button{
    margin-top: 25px;
    height: 55px;
    width: 140px;
    background: #000;
    color: white;  
}
label{
    display: block;
    margin: 25px 0 15px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 12px;
}
#preview h3{
    font-size: 35px;
}
#preview p{
    font-size:30px;
}
#preview{
    padding: 15px 25px;
    border: 1px dotted #000;
    margin: 35px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 0px;
}
#checkboxes p{
    font-size: 40px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 23px;
}
}
@media(min-width: 1500px){
#add-blog{
    background: url(./2f.jpg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
}
.date input[type="text"]{
    height: 40px;
    width: 225px;
    
}


#add-blog *{
    box-sizing: border-box;
}

#add-blog h2{
    margin-top: 20px;
    font-size: 85px;
    text-align: center;
    color: rgb(0, 0, 0);
}

#add-blog label{
    font-size: 60px;
}
#add-blog{
    margin: 5px auto;
    max-width: 1250px;
}
#add-blog button{
    margin-top: 25px;
    height: 75px;
    width: 190px;
    background: #000;
    color: white;  
    font-size: 25px;
}
label{
    display: block;
    margin: 25px 0 15px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 14px;
}
#preview h3{
    font-size: 45px;
}
#preview p{
    font-size:45px;
}
#preview{
    padding: 15px 25px;
    border: 1px dotted #000;
    margin: 35px 0;
    
}
#preview{
    word-wrap: break-word;
}
h3{
    margin-top: 45px;
}
#checkboxes input{
    display: inline-block;
    margin-right: 0px;
}
#checkboxes p{
    font-size: 60px;
}


#checkboxes label{
    display: inline-block;
    margin-top: 0;
    font-size: 35px;
}
}

</style>
