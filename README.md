# mvc-model-repository
Öncelikle "ImageUrl" eklediğimiz için de unutmuyoruz ki wwwroot klasörümüzün içine de img klasörü eklemeyi de unutmamalıyız. wwwroot/img<br>
Projemize model ve repository classları ekliyoruz.<br>
Movie.cs class dosyamızı oluşturuyoruz.
<pre>

using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace MovieApp.Models
{
    public class Movie
    {
        public int Id { get; set; }
        
        public string Name { get; set; }
        
        public string Description { get; set; }
        
        public string ImageUrl { get; set; }
    }
}

</pre>
```diff
-Sanal bir repository, sanal bir database yapısı oluşturuyoruz.
+Ekleme,Listeleme,Güncelleme,Silme vb.
```
Repository.cs class dosyamızı oluşturuyoruz.
<pre>
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace MovieApp.Models
{
    public static class Repository
    {
        private static List<Movie> _movies = null;

        static Repository()
        {
            _movies = new List<Movie>() { 
                new Movie() { Id=1, Name="Film Adı 1", Description="Film Açıklama 1", ImageUrl="1.jpg"},
                new Movie() { Id=2, Name="Film Adı 2", Description="Film Açıklama 2", ImageUrl="2.jpg"},
                new Movie() { Id=3, Name="Film Adı 3", Description="Film Açıklama 3", ImageUrl="3.jpg"},
                new Movie() { Id=4, Name="Film Adı 4", Description="Film Açıklama 4", ImageUrl="4.jpg"},
            };
        }

        public static List<Movie> Movies
        {
            get
            {
                return _movies;
            }
        }

        public static void AddMovie(Movie entity)
        {
            _movies.Add(entity);
        }

        public static Movie GetById(int id)
        {
            return _movies.FirstOrDefault(i => i.Id == id);
        }
    }
}

</pre>

