# birthday-starsfrom datetime import datetime, date
import calendar

# Ввод даты
day = int(input("День рождения: "))
month = int(input("Месяц рождения: "))
year = int(input("Год рождения: "))
birth_date = date(year, month, day)

# День недели
def get_weekday(d):
    return calendar.day_name[d.weekday()]  # Monday, Tuesday...

# Високосный год
def is_leap(y):
    return (y % 4 == 0 and y % 100 != 0) or (y % 400 == 0)

# Точный возраст
def get_age(birth):
    today = date.today()
    return today.year - birth.year - ((today.month, today.day) < (birth.month, birth.day))

# Вывод звёздочками (цифры 0-9 в формате 3x5)
digits = {
    '0': ["***","* *","* *","* *","***"],
    '1': [" * ","** "," * "," * ","***"],
    '2': ["***","  *","***","*  ","***"],
    '3': ["***","  *","***","  *","***"],
    '4': ["* *","* *","***","  *","  *"],
    '5': ["***","*  ","***","  *","***"],
    '6': ["***","*  ","***","* *","***"],
    '7': ["***","  *","  *","  *","  *"],
    '8': ["***","* *","***","* *","***"],
    '9': ["***","* *","***","  *","***"]
}

def print_big(day, month, year):
    s = f"{day:02d}{month:02d}{year:04d}"  # например, 15072006
    for row in range(5):
        line = ""
        for ch in s:
            line += digits[ch][row] + " "
        print(line)

# Результаты
print(f"День недели: {get_weekday(birth_date)}")
print(f"Високосный: {'Да' if is_leap(year) else 'Нет'}")
print(f"Возраст: {get_age(birth_date)} лет")
print("\nДата рождения звёздочками:")
print_big(day, month, year)