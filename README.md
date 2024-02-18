# Analogy
A project to create a platform of user based uploading. Users upload their very own explanations of certain topics.


    from random import randint
    """
    === Analogy Project ===
    Feb 16th 2024 - Feb 18th 2024
    Caroline P. & Claudia F."""


    class Analogy:
        points: int
        user_id: tuple
        topic: str
        content: str
  
        def __init__(self, user_id, content, topic):
            """Making a new analogy post

            Public Attributes:
            user_id : references to who is making the post
            content: What the user came up with
            """
            self.user_id = user_id
            self.content = content
            self.points = 0
            self.topic = topic

        def like_analogy(self):
            self.points += 1
  

    class Users:
        analogies: dict[Analogy]
        total_points: int
        user_id: tuple

        def __init__(self, analogies, user_id):
            """ Creating users:
  
            Public Attributes:
            analogies = a list of the analogies that user has made
            total_points = total points the user has gotten from their posts
            user_id = A tuple containing their username the user chooses, and
                      their user number that is given privately"""
            self.analogies = analogies
            accumulator = 0
            for analogy in analogies:
                accumulator += analogy.points
            self.total_points = accumulator
            self.user_id = user_id
  
        def best_analogy(self):
            """Returns the analogy or analogies of the ones with the most points"""
            most = 0
            the_one = []
            for an_analogy in self.analogies:
                if an_analogy.points > most:
                    most = an_analogy.points
                    the_one = [an_analogy]
                elif an_analogy.points == most:
                    the_one.append(an_analogy)
            return the_one
  
        def display_user(self):
            """prints statements of the information of the user"""
            print((self.user_id[0]) + "has an awesome analogy(s)!")
            best = self.best_analogy()
            for i in best:
                print("For example: " + best[i].topic)
                print(best[i].content)
            print("Total Points: " + best[i].total_points)
  
  
    class Collection:
        users = [Users]
        posts = [Analogy]

        def __init__(self, data):
            """Main database of all analogies"""
            self.data = data
            self.users = []
            self.posts = []

        def add_to_collection(self, new):
            if new.is_instance(Users):
                self.users += new
            elif new.is_instance(Analogy):
                self.users += new
  

    def search_users(user: str, data: Collection):
        for user in data.users:
            if user.user_id[0] == user:
                return user.display_user()
            return "No user found"


    def search_analogy(topic: str, data: Collection):
        for analogy in data.posts:
            if analogy.topic == topic:
                return analogy.topic
            return "No analogies for this topic yet"
