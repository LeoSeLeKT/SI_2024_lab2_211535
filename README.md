# SI_2024_lab2_211535
## Леонид Манески 211535
## Control Flow Graph

![SI lab2 cfg](https://github.com/LeoSeLeKT/SI_2024_lab2_211535/assets/94115888/5d70ff9f-34ab-4374-a872-edf6bc177d08)

## Цикломатска комплексност

M = E - N + 2P

каде:

E - број ребра во графот

N - број на темиња во графот

P - број на различни компоненти

така што, M = 32 - 24 + 2 = 10.

Што значи дека цикломатската комплексност на checkChart функцијата е 10



## Тест случаи според критериумот Every Statement

![табела си лаб2](https://github.com/LeoSeLeKT/SI_2024_lab2_211535/assets/94115888/db476478-7a29-44b2-a320-43d82651551d)

## Тест случаи според Multiple Condition критериумот за условот if (item.getPrice() > 300 && item.getDiscount() > 0 && item.getBarcode().charAt(0)== '0')
За позитивен тест случај, мора секој од следниве тест примери да биде позитивен, за да биде задоволен цел услов: item.getPrice() > 300 ; item.getDiscount() > 0 ; item.getBarcode().charAt(0)=='0'

Додека, ако барем еден од следниве услови се исполнува, условот ќе е негативен: item.getPrice()<=300 ; item.getDiscount()<=0 ; item.getBarcode().charAt(0)!='0'


