
class QuizGame:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0

    def display_welcome_message(self):
        print("Welcome to the Fill-in-the-Blank Quiz Game!")
        print("You'll be presented with sentences with missing words.")
        print("Your task is to fill in the blanks correctly.\n")

    def present_quiz_questions(self):
        for i, question in enumerate(self.questions, 1):
            print(f"Question {i}: {question['question']}")
            user_answer = input("Your answer: ")
            self.evaluate_answer(user_answer, question['answer'])

    def evaluate_answer(self, user_answer, correct_answer):
        if user_answer.lower() == correct_answer.lower():
            print("Correct!")
            self.score += 1
        else:
            print("Incorrect!")
            print(f"The correct answer is: {correct_answer}\n")

    def display_final_results(self):
        print("\nQuiz completed!")
        print(f"Your final score is: {self.score}/{len(self.questions)}")
        if self.score == len(self.questions):
            print("Congratulations! You got a perfect score!")
        elif self.score >= len(self.questions) / 2:
            print("Well done! You did pretty well.")
        else:
            print("You might want to brush up on your knowledge.")

    def play_again(self):
        choice = input("Do you want to play again? (yes/no): ")
        return choice.lower() == 'yes'

questions = [
    {
        'question': "The capital of Italy is ____________.",
        'answer': "Rome"
    },
    {
        'question': "The largest ocean in the world is the ____________ Ocean.",
        'answer': "Pacific"
    },
    {
        'question': "The currency of Japan is the ____________.",
        'answer': "yen"
    }
]
# Main function to run the quiz
def main():
    game = QuizGame(questions)
    game.display_welcome_message()
    game.present_quiz_questions()
    game.display_final_results()
    while game.play_again():
        game.score = 0
        game.present_quiz_questions()
        game.display_final_results()

if __name__ == "__main__":
    main()

