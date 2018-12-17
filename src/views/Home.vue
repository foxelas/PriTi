
<template>
  <v-layout justify-center>
    <v-flex xs12 sm6>
      <v-card>
        <v-container
          fluid
          grid-list-md
        >
          <v-layout row wrap>
            <v-flex>
              <v-card>
                <v-img
                  :src="kidsCard.src"
                  height="200px"
                >
                  <v-container
                    fill-height
                    fluid
                    pa-2
                  >
                    <v-layout fill-height>
                      <v-flex xs12 align-end flexbox>
                        <span class="headline white--text" v-text="kidsCard.title" ></span>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-img>
              </v-card>
            </v-flex>

			<v-flex xs6 align-end flexbox>
				<v-card color="cyan darken-2" class="white--text ext-xs-center" height="250px">
						<v-card-title>
							Try PriTi~!
						</v-card-title>
						<v-card-text>
							PriTi is the service that you always needed!
							We will help you find a foreign Private Tutor, able to teach you using their native language.
							You can explore your options based on location, price and time availability. 
							You can also request a tutor for a specific course.
						</v-card-text>
						<v-card-actions>
							<v-btn dark large round justify="justify-right" router to="/tutors" color="success">Explore promoted Tutors</v-btn>
						</v-card-actions>

				</v-card>
			</v-flex>

			<v-flex>
				<v-card height="250px">
				<v-container
                    fill-height
                    fluid
					pa-0
                  >
                    <v-layout fill-height>
						<v-carousel hide-controls hide-delimiters height="100%">
								<v-carousel-item
								v-for="tutor in promotedTutors"
								:src="tutor.imageUrl" 
								:key="tutor.id">
								</v-carousel-item>	         
						</v-carousel>
				    </v-layout>
				</v-container>	
				</v-card>	
            </v-flex>

			<v-flex xs12 flexbox>
									
				<v-card>
				<v-carousel>
					
					<v-carousel-item 
					v-for="course in promotedCourses"
					:src="course.imageUrl"
					:key="course.id">
					<v-layout fill-height align-end justify-center pb-5>
						<v-btn  color="indigo" round v-on:click="goToCoursesPage(course.name)">								
						{{ course.title }}
						</v-btn>
					</v-layout>
					</v-carousel-item>	 
				</v-carousel>
				</v-card>
									
			</v-flex>	

          </v-layout>
        </v-container>
      </v-card>
    </v-flex>
  </v-layout>
</template>


<script>

	export default {
		data: () =>({
			kidsCard: {
				title:"Are you a student in an international school in Tokyo?",
				flex: "",
				src: "https://www.smis.ac.jp/uploaded/photos/academics/academics-intro-5.jpg",
			},
			promotedCourses: [
					{ imageUrl:'http://www.mrbartonmaths.com/blog/wp-content/uploads/2017/06/june.png', id:'wda',title:'Courses in Biology', name: "biology"},
					{ imageUrl:'https://www.insidescience.org/sites/default/files/sites/default/files/images/articles/top-images/2018/physics-chalkboard_cropped.jpg', id:'wdwd',title:'Courses in mathematics', name:"mathematics"}
				],
				promotedTutors: [
					{
						id:1,
						name: "Michael",
						imageUrl: "https://i.imgur.com/jJVDi0G.jpg" 
					},
					{
						id:2,
						name: "Yulia",
						imageUrl: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTYIXDFOqEC6RWIQJ2j9aOEavfQeRb1U9xtt4Z5O6-WFGDoA-bxRw" 
					},
					{
						id:3,
						name: "Chen",
						imageUrl: "http://image2.sina.com.cn/ent/d/2001-07-31/28-3-52024_09.jpg" 
					},
				]
		}),
	  methods: {
			goToCoursesPage: function (courseName){
				console.log()
				this.$router.push('/courses/' + courseName);
			},
		}
	}
</script>

<style scoped>
	.title {
		position: absolute;
		bottom: 50px;
		background-color: rgba(0,0,0,0.5);
		color: white;
		font-size: 2em;
		text-align: center
	}
</style>
