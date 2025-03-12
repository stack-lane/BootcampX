# Assignment #002 <br/> Movies

> This assignment is due by 12:30 PM, 12 March 2025.
>
> Once you've completed your assignment, submit it over [here](https://forms.gle/UGD9m8wps1r5rL7y5).

Create a series of methods as below for a for a Movies Management system.

- `addMovie(...)` — Add a movie with properties: id, title, director, releaseYear, genre.
- `rateMovie(id: string, rating: number)` — Rate a movie (1-5 stars).
- `getAverageRating(id: string): number | undefined` — Get average rating of a movie.
- `getTopRatedMovies()` — Returns movies sorted by highest rating.
- `getMoviesByGenre(genre: string)` — Get all movies of a genre.
- `getMoviesByDirector(director: string)` — Get all movies by a director.
- `searchMoviesBasedOnKeyword(keyword: string)` - Get all movies that contain the given `keyword` in their `title` property.
- `getMovie(id: string)` — Get movie details.
- `removeMovie(id: string)` — Remove a movie.
