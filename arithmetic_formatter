
def validate_problems(problems):
    if len(problems) > 5:
        return 'Error: Too many problems.'

    for problem in problems:
        parts = problem.split()
        if '+' not in problem and '-' not in problem:
            return "Error: Operator must be '+' or '-'."
        if not parts[0].isdigit() or not parts[2].isdigit(): 
            return 'Error: Numbers must only contain digits.'
        for part in parts:
            if len(part) > 4:
                return 'Error: Numbers cannot be more than four digits.'
    return None


def split_problems(problems):
    return [problem.split() for problem in problems]
    
def evaluate_problems(problem_parts):
    return [int(part[0]) + int(part[2]) if part[1] == '+' else int(part[0]) - int(part[2]) for part in problem_parts]

def format_problem_lines(problem_parts,results):
    first_operands = [part[0] for part in problem_parts]
    operators = [part[1] for part in problem_parts]
    second_operands = [part[2] for part in problem_parts]

    most_digits = [max(len(first),len(second)) for first, second in zip(first_operands, second_operands)]
    dashes_needed = [2 + digits for digits in most_digits]

    spaces_needed_1 = [dashes - len(operand) for dashes, operand in zip(dashes_needed, first_operands)]
    spaces_needed_2 = [dashes - len(operand) -1 for dashes, operand in zip(dashes_needed, second_operands)]
    spaces_needed_3 = [dashes - len(str(result)) for dashes, result in zip(dashes_needed, results)]
        
    return first_operands, operators, second_operands, dashes_needed, spaces_needed_1, spaces_needed_2, spaces_needed_3

def arithmetic_arranger(problems, show_answers=False):
    error = validate_problems(problems)
    if error:
        return error

    problem_parts = split_problems(problems)
    results = evaluate_problems(problem_parts)
    
    first_operands, operators, second_operands, dashes_needed, spaces_needed_1, spaces_needed_2, spaces_needed_3 = format_problem_lines(problem_parts,results)

    line_1 = "    ".join([f"{spaces_needed_1[i] * ' '}{first_operands[i]}" for i in range(len(problems))])
    line_2 = "    ".join([f"{operators[i]}{spaces_needed_2[i] * ' '}{second_operands[i]}" for i in range(len(problems))])
    line_3 = "    ".join([f"{dashes_needed[i] * '-'}"  for i in range(len(problems))])
    line_4 = "    ".join([f"{spaces_needed_3[i] * ' '}{results[i]}" for i in range(len(problems))])

    if  show_answers == True:
        return f"{line_1}\n{line_2}\n{line_3}\n{line_4}"
    else:
        return f"{line_1}\n{line_2}\n{line_3}"
    

print(f'\n{arithmetic_arranger(["32 - 698", "1 - 3801", "45 + 43", "123 + 49", "988 + 40"], True)}')