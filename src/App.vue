<template>
  <div>
    <h1>Bind Data Property: Mustache syntax, v-text directives</h1>
    <h4>Hello {{ name }}</h4>
    <h4 v-text="channel"></h4>
    <hr>

    <h2>Bind Raw html: v-html directive</h2>
    <h4 v-html="boldText"></h4>
    <hr>

    <h3>Bind attribute: v-bind directives(v-bind:attr="property")</h3>
    <p v-bind:id="headerid">heading</p>
    <button v-bind:disabled="isDisabled">disable</button>
    <hr>

    <h3>Bind class: v-bind directives(v-bind:class="classname")</h3>
    <p class="static">static class</p>
    <p v-bind:class="success">dynamic class binding</p>
    <p class="static" v-bind:class="success">static and dynamic class binding</p>
    <p v-bind:class="iscondition ? 'success' : 'danger' ">conditional class binding</p>
    <p v-bind:class="['new', 'promoted']">array class binding</p>
    <p v-bind:class="[isPromoted && 'promoted', isNew ? 'success' : 'danger']">array conditional class binding</p>
    <p v-bind:class="{
      promoted: isPromoted,
      success: isNew,
      danger: !isNew
    }">object conditional class binding</p>
    <hr>

    <h3>inline style binding</h3>
    <p v-bind:style="{color: highLightColor}">single property</p>
    <p v-bind:style="styleObject">Multiple Property</p>
    <p v-bind:style="[baseStyleObject, successStyleObject]">array inlie style</p>
    <hr>

    <!-- ================= if else show condition =============== -->
    <h3>if else show condition</h3>
    <p v-if="isShow">show it if it is true</p>
    <p v-else-if="!isShow">show if it is false</p>
    <p v-else>show it</p>

    <!-- multiple element show -->
    <template v-if="isMultiple">
      <p>one</p>
      <p>two</p>
    </template>

    <!-- show/hide toggle but exist into dom -->
    <p v-show="isShow">hide but exist into DOM</p>
    <hr>

    <!-- ============= List Rendaring =============== -->
    <div v-bind:class="wrapper">
      <h1 v-bind:style="{borderBottom: '2px solid green'}">List Rendering</h1>

      <div v-bind:class="subTopic">
        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-for directives, key attr: array of strings</h2>
        <p v-for="(name, index) in names" v-bind:key="name"> {{index}}-{{ name }}</p>
      </div>

      <div v-bind:class="subTopic">
        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-for directives, key attr: array of object</h2>
        <p v-for="name in fullNames" v-bind:key="name.first"> {{ name.first }} {{ name.last }}</p>
      </div>
      
      <div v-bind:class="subTopic">
        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-for directives, key attr: array of array </h2>
        <div v-for="student in students" v-bind:key="student.name">
          <h6>{{ student.name}}</h6> has <p v-for="subject in student.subjects" v-bind:key="subject">{{ subject }}</p>
        </div>
      </div>

      <div v-bind:class="subTopic">
        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-for directives, key attr: object</h2>
          <p v-for="info in info" v-bind:key="info">{{ info }}</p>
      </div>
    </div>

    <!-- ============= Conditional List Rendaring =============== -->
    <div v-bind:class="wrapper">

      <h1 v-bind:style="{borderBottom: '2px solid green'}">Conditional List Rendering</h1>

      <div v-bind:class="subTopic">
        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-for and v-if directives, key attr: use template tag</h2>
        <template v-for="name in names" :if="name === 'ami'"> {{ name }} </template>
      </div>

    </div>

    <!-- ============= Methods Rendaring =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Methods Rendering</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Methods: normal func not arrow func</h2>

        <p>{{ add() }}</p>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Methods(this kewword): Data Property as variable into methods body</h2>

        <p>{{ multiply() }}</p>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Methods(without this kewword): Data Property as argument</h2>

        <p>{{ multArg(baseValue) }}</p>

      </div>

    </div>

    <!-- ============= Event handling =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Event handling</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-on directives: inline event </h2>

        <h3>{{ name }}</h3>
        <button v-on:click="name = 'react'">click to change name</button>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-on directives: Event as method </h2>

        <h3>{{ count }}</h3>
        <button v-on:click="increMent()">increment</button>
        <button v-on:click="decreMent()">decrement</button>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">short hand : v-on: -> @ </h2>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">event object as single argument: methodname </h2>

        <h3>{{ name }}</h3>
        <button v-on:click="changeName">changename and log event object</button>

      </div>
      
      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">event object as second argument: $event </h2>

        <h3>{{ count }}</h3>
        <button v-on:click="increMentByNum(2, $event)">increment and log event object</button>

      </div>
      
      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Multiple Event: comma seperated method </h2>

        <h3>{{ name }}</h3>
        <h3>{{ count }}</h3>
        <button v-on:click="changeName($event), increMentByNum(2, $event)">increment and log event object</button>

      </div>

    </div>

    <!-- ============= Form handling =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Event handling</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-model directives: two way binding- template to data properties</h2>

        <div>
          <pre>
            {{ JSON.stringify(formvalues, null, 2) }}
          </pre>
        </div>

        <form @submit="formSubmit">

          <div>
            <label for="name">Name:</label>
            <input type="text" name="name" id="name" v-model.trim="formvalues.name">
          </div>

          <div>
            <label for="profile">Profile:</label>
            <textarea name="profile" id="profile" v-model="formvalues.profilesummary"></textarea>
          </div>

          
          <div>
            <label for="country">Country</label>
            <select name="country" id="country" v-model="formvalues.country">
              <option value="">Select Country</option>
              <option value="Bangladesh">Bangladesh</option>
              <option value="Arab">Arab</option>
            </select>
          </div>

          <div>
            <label for="job-location">Job Location</label>
            <select name="job-location" multiple id="job-location" v-model="formvalues.joblocation">
              <option value="">Select Country</option>
              <option value="Bangladesh">Bangladesh</option>
              <option value="Arab">Arab</option>
              <option value="Singapore">Singapore</option>
            </select>
          </div>

          <div>
            <input type="checkbox" name="remotework" id="remotework" v-model="formvalues.remotework" true-value="yes" false-value="no">
            <label for="remotework">Open to remote work?</label>
          </div>

          <div>
            <label for="">Skill set: </label>
            <input type="checkbox" name="html" id="html" value="html" v-model="formvalues.skillset">
            <label for="html">HTML</label>
            <input type="checkbox" name="css" id="css" value="css" v-model="formvalues.skillset">
            <label for="css">CSS</label>
            <input type="checkbox" name="javascript" id="javascript" value="javascript" v-model="formvalues.skillset">
            <label for="javascript">JavaScript</label>
          </div>

          <div>
            <label for="">Years of Experience: </label>
            <input type="radio" name="0-2" id="0-2" value="0-2" v-model="formvalues.yearsOfExperience">
            <label for="0-2">0-2</label>
            <input type="radio" name="3-5" id="3-5" value="3-5" v-model="formvalues.yearsOfExperience">
            <label for="3-5">3-5</label>
            <input type="radio" name="6-10" id="6-10" value="6-10" v-model="formvalues.yearsOfExperience">
            <label for="6-10">6-10</label>
            <input type="radio" name="10+" id="10+" value="10+" v-model="formvalues.yearsOfExperience">
            <label for="10+">10+</label>
          </div>

          <div>
            <label for="age">Age</label>
            <input type="number" name="age" id="age" v-model.number="formvalues.age">
          </div>

          <div>
            <button type="submit">Submit</button>
          </div>

        </form>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">v-model / v-on modifiers: v-model.modifiername=" "</h2>
        <p>v-model.trim</p>
        <p>v-model.number</p>
        <p>v-model.lazy</p>
        <p>v-on.prevent</p>
        <p>v-on.keyup  or like others</p>

      </div>

    </div>

    <!-- ============= Computed Prperties =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Computed Prperties</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Computed Properties: similar to data properties & create new data from existing source</h2>

        <p>Computed Fullname - {{ fullName }}</p>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Uses: it returns cashed values. It is more performant other than methods</h2>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Conditional rendering</h2>

        <p v-for="item in expenSiveItem" :key="item.id">{{ item.title }} - {{ item.price }}</p>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Getter & Setter: get() & set()</h2>
        <p>{{ fullName }}</p>
        <button @click="changeNames">Chane Full Name</button>

      </div>

    </div>

    <!-- ============= Watchers =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Watchers</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Alow to watch data / property and execute code in response to changes value</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>wathchers execute when data is changed</li>
          <li>in watch property make a method according to name as data property </li>
          <li>automatic give new & old value as argument</li>
        </ul>

        <h3>Volume Tracker (0-20)</h3>
        <h4>Current Volume - {{ volume }}</h4>
        <div>
          <button @click="volume += 2">Increase</button>
          <button @click="volume -= 2">Decrease</button>
        </div>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">watchers: handler, immediate(boolean) - Calling Watchers during page load</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>immidiate & handler: calling watchers during page load (like API call) </li>
          <li>-> create object according to data property name</li>
          <li>-> this object has handler property as method</li>
          <li>-> this object has immediate property as string</li>
        </ul>

        <input type="text" name="movie" id="movie" v-model="movie">

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">watchers: handler, deep(boolean) - in regards object</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>deep & handler: in regards Object </li>
          <li>-> create object according to data property name</li>
          <li>-> this object has handler property as method</li>
          <li>-> this object has deep property as string</li>
        </ul>
        <br>
        <input type="text" name="title" id="title" v-model="movieInfo.title">
        <input type="text" name="actor" id="actor" v-model="movieInfo.actor">

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">watchers: handler, deep(boolean) - in regards Array</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>deep & handler: in regards array mutating </li>
          <li>-> create object according to data property name</li>
          <li>-> this object has handler property as method</li>
          <li>-> this object has deep property as string</li>
          <li>** for refferencing array deep is not required</li>
        </ul>
        <br>
        <div>
          <button @click="movieList.push('Wonder Women')">Add Movie</button>
        </div>

      </div>

    </div>

    <!-- ============= Components =============== -->
    <div v-bind:class="wrapper">
      
      <h1 v-bind:style="{borderBottom: '2px solid green'}">Components</h1>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Basic Components</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>create file as filename.vue into components folder</li>
          <li>--> template, script &style tag</li>
          <li>--> export this component </li>
          <li>--> import that component into root app component</li>
          <li>--> register component tag in root component</li>
          <li>--> finally pass this props into template in child component</li>
        </ul>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Static Props as attribute</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>create component</li>
          <li>cretae "props array" into child component</li>
          <li>register component tag with props in root component</li>
          <li>pass this props into template in child component</li>
        </ul>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Dynamic Props as attribute</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>create component</li>
          <li>cretae props array into child component</li>
          <li>create data property into root component</li>
          <li>pass this property as props value into root component</li>
          <li>register component tag with ":propsname" as attribute in root component</li>
          <li>pass this props into template in child component </li>
        </ul>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">non prop attribute - having no property defined in props</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>example: id, class, style etc.</li>
          <li>where to be added use : v-bind="$attrs"</li>
          <li>to disable default behaviour add: inheritAttrs: false as property into child component</li>
        </ul>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Nesting Components: passing(provide/inject) property to nested child component only</h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>create provide object & property inside provide object in root component</li>
          <li>create inject array in child component</li>
          <li>finally bind this property in child component</li>
        </ul>

      </div>

      <div v-bind:class="subTopic">

        <h2 v-bind:style="{borderBottom: '2px solid #999999', color: '#999999'}">Nesting Components: passing(provide/inject) property both in nested child and root component </h2>

        <ul v-bind:style = "{display: 'inline-block', color: '#999999', textAlign: 'left'}">
          <li>create data property in root component</li>
          <li>create provide method with return object in root component</li>
          <li>create property having value as data property in root component</li>
          <li>create inject array containing provide property in child component</li>
          <li>finally bind this property in child & root component</li>
        </ul>

      </div>

    </div>

    <!-- register greet component -->
    <Greet name="Tahidul" heroname="batman" />
    <Greet name="Abdullah" heroname="superman"/>

    <Greet :name="num" :heroname="channelname"/>

    <Article id="my-article" />

    <h2>App Component username {{ myName }}</h2>
    <ComponentC />

  </div>
</template>

<script>
import Greet from "./components/Greet.vue";
import Article from "./components/Article.vue";
import ComponentC from "./components/ComponentC.vue";

export default {
  name: 'App',
  components: {
    Greet,
    Article,
    ComponentC,
  },
  data () {
    return {
      name: 'Vue',
      // wrapper style
      wrapper: 'wrapper',
      // sub topic
      subTopic: 'subTopic',
      channel: 'codevolution',
      boldText: '<b>bold text</b>',
      headerid: 'heading',
      isDisabled: true,
      success: 'success',
      iscondition: false,
      isPromoted: true,
      isNew: true,
      styleObject: {
        color: 'orange',
        fontSize : 50 + 'px'
      },
      baseStyleObject: {
        fontSize: '20px',
        padding: '10px'
      },
      successStyleObject:{
        color:'green',
        backgroundColor: 'lightGreen',
        border: '1px solid green'
      },
      isShow: false,
      isMultiple: true,
      // for list rendering
      names: ['ami', 'tumi', 'se'],
      fullNames: [
        {first: 'titu', last:'ali'},
        {first: 'mitu', last:'mali'}
      ],
      students: [
        {
          name: 'safi',
          subjects: ['physics']
        },
        {
          name: 'Ovi',
          subjects: ['physics', 'mathematics']
        }
      ],
      info: {
        name: 'tahidul',
        inst: 'Physics NINJA',
        sub: 'physics'
      },
      // for methods
      baseValue: 5,

      // for event handling
      count: 0,
      // for form handling
      formvalues: {
        name: '',
        profilesummary: '',
        country: '',
        joblocation: [],
        remotework: 'no',
        skillset: [],
        yearsOfExperience: '',
        age: ''
      },
      // computed full name
      firstname: 'abdullah',
      lastname: 'titu',
      items: [
        {
          id: 1,
          title: 'mouse',
          price: 100
        },
        {
          id: 2,
          title: 'Laptop',
          price: 200
        },
        {
          id: 3,
          title: 'keyboard',
          price: 300
        }
      ],
      // for watchers
      volume: 0,
      movie: 'Batman',
      movieInfo: {
        title: '',
        actor:'',
      },
      movieList: ['Batman', 'Suoerman'],
      // for dynamic props
      num: 'muhammad',
      channelname : 'codevolution',
      // for nestede component
      myName: "Abdullah",
    }
  },
  methods: {
    // methods
    add() {
      return 'hello';
    },
    multiply () {
      return 5 * this.baseValue;
    },
    multArg(num) {
      return 5 * num;
    },
    // event handling
    increMent () {
      return this.count += 1;
    },
    decreMent () {
      return this.count -= 1;
    },
    changeName(e) {
      this.name = 'React';
      console.log('event', e);
    },
    increMentByNum (num, e) {
      this.count += num;
      console.log(e);
    },
    // form submit
    formSubmit (e) {
      e.preventDefault();
      console.log("Form valuse: ", this.formvalues);
    },
    // computed getter setter
    changeNames() {
      return this.changefullName = 'Tahidul Islam';
    }

  },
  computed: {
    fullName () {
      return `${this.firstname} ${this.lastname}`;
    },
    expenSiveItem () {
      return this.items.filter( item => item.price > 100 );
    },
    changefullName: {
      get(){
        return `${this.firstname} ${this.lastname}`;
      },
      set(value) {
        const name = value.split(' ');
        this.firstname = name[0];
        this.lastname = name[1];
      }
    }
  },
  watch: {
    volume(newvolume, oldvolume) {
      if (newvolume > oldvolume &&  newvolume === 16) {
        alert('value is 16');
      }
    },
    movie: {
      handler(newValue) {
        console.log(`Calling API with Movie name - ${newValue}`);
      },
      immediate: true,
    },
    movieInfo: {
      handler(newValue) {
        console.log(`Calling API for movie info title - ${newValue.title} ad actor - ${newValue.actor} `);
      },
      deep:true
    },
    movieList: {
      handler(newValue) {
        console.log(`Updated movie list ${newValue}`);
      },
      deep: true,
    },
  },
  provide() {
    return {
      username: this.myName,
    }
  }
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.success {
  color: darkgreen;
}
.danger {
  color: red;
}
.wrapper {
  background-color: lightgreen;
  padding: 15px;
  border: 1px solid darkgreen;
  color: darkgreen;
  margin-bottom: 30px;
}
.subTopic {
  max-width: 600px;
  margin: 0 auto 15px auto;
  background: #e7e7e7;
  border: 2px solid #999999;
  padding: 0 15px;
}
</style>
