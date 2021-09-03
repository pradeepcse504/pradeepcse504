public interface IBake
    {
        string Name { get; }
        double Price { get; }
   }
public class BakeBase : IBake
    {
        private string m_Name = "Cake Base";
        private double m_Price = 200.00;

        public string Name
        {
            get 
            {
               return m_Name;
            }
        }

        public double Price
        {
            get
            {
                return m_Price;
            }
        }

         public string GetCakeCost()
        {
            return "Normal cake is:" + m_Price + "and Tax is: " + (this.m_Price * 0.08f);
        }
        }
class CherryDecorator
{
    IBake _iBakeModel;

    public CherryDecorator(IBake iBakeModel)            
    {
        _iBakeModel = iBakeModel;
    }

    public string GetName()
    {
        return "Cherry Decorated Cake!";
    }
    public double GetPrice()
    {
        return _iBakeModel.Price + 100;
    }
    }
class CreamDecorator
    {
        IBake _iBakeModel;
        public CreamDecorator(IBake iBakeModel)            
        {
            _iBakeModel = iBakeModel;
        }
         public string GetName()
        {
          return "Cream Decorated Cake!";
          }
        public double GetPrice()
        {
        return _iBakeModel.Price + 50;
      }
 }
 public class Client
{
static void Main(string[] args)
{

    BakeBase bakebase = new BakeBase();
    Console.WriteLine(bakebase.GetCakeCost());
    Console.ReadKey();
    Console.WriteLine(Environment.NewLine);
    CherryDecorator cd = new CherryDecorator(bakebase);
    Console.WriteLine(cd.GetName() + "  " + cd.GetPrice());
    Console.ReadKey();

    Console.WriteLine(Environment.NewLine);
    CreamDecorator crd = new CreamDecorator(bakebase);
    Console.WriteLine(crd.GetName() + "  " + crd.GetPrice());
    Console.ReadKey();
}
}
