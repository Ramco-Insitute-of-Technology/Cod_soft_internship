Build a simple chatbot that responds to user inputs based on predefined rules. Use if-else statements or pattern matching techniques to identify user queries and provide appropriate responses. This will give you a basic understanding of natural language processing and conversation flow.

#program code
import re
def simple_chatbot(user_input):
    user_input = user_input.lower()
    rules_and_responses = {
        'hello': 'Hi there! How can I help you?',
        'how are you': 'I am just a computer program, but thanks for asking!',
        'goodbye': 'Goodbye! Have a great day!',
        'thanks': 'You\'re welcome!',
        'favorite color': 'I don\'t have a favorite color. I\'m just a chatbot!',
        'calculate': calculate_expression,
        'default': "I'm sorry, I don't understand that. Can you please rephrase or ask something else?",
    }
    for pattern, response in rules_and_responses.items():
        if pattern in user_input:
            if callable(response):
                return response(user_input)
            else:
                return response
    return rules_and_responses['default']

def calculate_expression(user_input):
    match = re.search(r'calculate\s(.+)', user_input)
    
    if match:
        expression = match.group(1)
        
        try:
            result = eval(expression)
            return f'The result of {expression} is {result}.'
        except Exception as e:
            return f'Error calculating expression: {str(e)}'
    else:
        return 'Invalid calculation request. Please provide a valid mathematical expression.'
while True:
    user_input = input("You: ")

    if user_input.lower() == 'exit':
        print("Chatbot: Goodbye!")
        break

    response = simple_chatbot(user_input)
    print("Chatbot:", response)
