---
title: Interview Stuff
description: 
published: true
date: 2022-03-22T22:23:43.133Z
tags: backend, interviewing
editor: markdown
---

# Inversion Of Control
## Example
This is a component that provides a list of movies directed by a particular director.
### Naive Implementation
```
class MovieLister {
  public Movie[] moviesDirectedBy(String arg) {
      List allMovies = finder.findAll();
      for (Iterator it = allMovies.iterator(); it.hasNext();) {
          Movie movie = (Movie) it.next();
          if (!movie.getDirector().equals(arg)) it.remove();
      }
      return (Movie[]) allMovies.toArray(new Movie[allMovies.size()]);
  }
```
### Decoupling Listing logic from storage
Ideally, the `moviesDirectedBy` method should be completely independent of how the movies are being stored. So, all the method should do is refer to a finder, and all the finder does is know how to execute the `findAll` method. 

```
public interface MovieFinder {
	List findAll();
}
```

```
class MovieLister {
  private MovieFinder finder;
  public MovieLister() {
    finder = new ColonDelimitedMovieFinder("movies1.txt");
  }
```
#### Dependency Issues
![ioc_dependencies_1.png](/ioc_dependencies_1.png)
Above, we see the dependencies for this situation. The MovieLister class is dependent on both the MovieFinder interface and it's implementation. Ideally, the MovieLister class would be dependent only on the interface... but then how do we make an instance to work with?

