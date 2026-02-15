class Reporting:
    def __init__(self):
        self.monthly_sales = {}

    def record_sale(self, month, pass_type, amount):
        if month not in self.monthly_sales:
            self.monthly_sales[month] = {
                "WeeklyPass": 0,
                "MonthlyPass": 0,
                "SingleEntryPass": 0
            }

        self.monthly_sales[month][pass_type] += amount

    def generate_monthly_report(self, month):
        if month not in self.monthly_sales:
            print("No sales data for this month.")
            return

        data = self.monthly_sales[month]
        total = sum(data.values())

        print(f"\n**{month} Monthly Sales Report**")
        print(f"Weekly Pass  : ${data['WeeklyPass']}")
        print(f"Monthly Pass : ${data['MonthlyPass']}")
        print(f"Single Entry : ${data['SingleEntryPass']}")
        print(f"Total Sales  : ${total}")
