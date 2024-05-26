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

##Unit test
 1. За секој тест за кој проверуваме дали во одреден дел се фрла исклучок.
2. Фрлениот исклучок го зачувуваме во променлива.
3. Проверуваме дали тој исклучок ја содржи истата порака како и во главниот код.

{

    @Test
    public void Every_Statement() {

        //testNullItems
        List<Item> allItems = null;
        RuntimeException ex;
        ex = Assertions.assertThrows(RuntimeException.class, () -> SILab2.checkCart(allItems, 100));
        Assertions.assertTrue(ex.getMessage().contains("allItems list can't be null!"));

        //testItemsWithoutName
        List<Item> itemsWithNameNull = Arrays.asList(
                new Item(null, "12345", 50, 0.1F),
                new Item("", "67890", 100, 0.0F)
        );
        Assertions.assertDoesNotThrow(() -> SILab2.checkCart(itemsWithNameNull, 100));
        Assertions.assertFalse(() -> SILab2.checkCart(itemsWithNameNull, 100));

        //testNullBarcode
        List<Item> itemsWithBarcodeNull = Arrays.asList(
                new Item("Item1", null, 50, 0.1F),
                new Item(null, "12345", 50, 0.1F)

        );
        ex = Assertions.assertThrows(RuntimeException.class, () -> SILab2.checkCart(itemsWithBarcodeNull, 100));
        Assertions.assertTrue(ex.getMessage().contains("No barcode!"));

        //testInvalidBarcode
        List<Item> itemsWithInvalidBarcode = Arrays.asList(
                new Item("Item1", "123A45", 50, 0.1F),
                new Item("Item2", "67890", 100, 0.0F)
        );
        ex = Assertions.assertThrows(RuntimeException.class, () -> SILab2.checkCart(itemsWithInvalidBarcode, 100));
        Assertions.assertTrue(ex.getMessage().contains("Invalid character in item barcode!"));

        //testSpecialDiscount
        List<Item> itemsForSpecialDiscount = Arrays.asList(
                new Item("Item1", "012345", 400, 0.1F),
                new Item("Item2", "12345", 200, 0.1F)
        );
        Assertions.assertTrue(SILab2.checkCart(itemsForSpecialDiscount, 1000));

    }

    @Test
    public void testSpecialDiscountCondition(){
        List<Item> allItems = Arrays.asList(
                new Item("Product A", "012345", 400, 0.2f),
                new Item("Product B", "123456", 200, 0.1f),
                new Item("Product C", "034567", 500, 0.25f)
        );

        float expectedSum = (float) ((400*0.2F)-30 + (200*0.1F) + (500*0.25)-30);

        Assertions.assertTrue(SILab2.checkCart(allItems,(int)expectedSum));

    }

}
