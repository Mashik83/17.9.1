sequence_of_numbers = [int(x) for x in input("Введите числа через пробел : ").split()]

print(sequence_of_numbers)

while True:
try:
number = int(input("Введите число от 2 до 499: "))
if number < 1 or number > 500:
raise Exception
break
except ValueError:
print("Веедите число!")
except Exception:
print("Неверный диапазон!")

array = sequence_of_numbers + [number]

def merge_sort(array):
if len(array) < 2:
return array[:]
else:
middle = len(array) // 2
left = merge_sort(array[:middle])
right = merge_sort(array[middle:])
return merge(left, right)

def merge(left, right):
result = []
i, j = 0, 0

while i < len(left) and j < len(right):
if left[i] < right[j]:
result.append(left[i])
i += 1
else:
result.append(right[j])
j += 1

while i < len(left):
result.append(left[i])
i += 1

while j < len(right):
result.append(right[j])
j += 1

return result

print(merge_sort(array), type(array))

def binary_search(array, number, left, right):
if left > right:
return False

middle = (right + left) // 2
if array[middle] == number:
return middle
elif number < array[middle]:
return binary_search(array, number, left, middle - 1)
else:
return binary_search(array, number, middle + 1, right)

print(binary_search(array, number, 0, len(array)))
