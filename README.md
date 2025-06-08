using System;


namespace TestTime

{

    public struct Time

    {

        private readonly int minutes;


        // Constructor from hours and minutes

        public Time(int hh, int mm)

        {

            this.minutes = 60 * hh + mm;

        }


        // Constructor from total minutes

        public Time(int totalMinutes)

        {

            this.minutes = totalMinutes;

        }


        // Read-only property to get the hour part

        public int Hour => minutes / 60;


        // Read-only property to get the minute part

        public int Minute => minutes % 60;


        // Overload + operator

        public static Time operator +(Time t1, Time t2)

        {

            return new Time(t1.minutes + t2.minutes);

        }


        // Overload - operator

        public static Time operator -(Time t1, Time t2)

        {

            return new Time(t1.minutes - t2.minutes);

        }


        public override string ToString()

        {

            // Return the time in hh:mm format with leading zeros if needed

            return String.Format("{0:D2}:{1:D2}", Hour, Minute);

        }

    }


    class Program

    {

        static void Main(string[] args)

        {

            Time morningTime = new Time(10, 5);   // 10:05 AM

            Time earlyTime = new Time(0, 45);     // 00:45 AM

            Time noonTime = new Time(12, 0);      // 12:00 PM

            Time nightTime = new Time(23, 45);    // 11:45 PM


            Console.WriteLine("Morning time: " + morningTime);

            Console.WriteLine("Early time: " + earlyTime);

            Console.WriteLine("Noon time: " + noonTime);

            Console.WriteLine("Night time: " + nightTime);


            Console.WriteLine("Night time hour: " + nightTime.Hour);

            Console.WriteLine("Night time minute: " + nightTime.Minute);


            // Test overloaded operators

            Time addedTime = morningTime + earlyTime;

            Time subtractedTime = nightTime - morningTime;


            Console.WriteLine("Added Time (morning + early): " + addedTime);

            Console.WriteLine("Subtracted Time (night - morning): " + subtractedTime);

        }

    }

}
