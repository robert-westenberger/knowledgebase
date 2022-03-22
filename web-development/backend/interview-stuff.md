---
title: Interview Stuff
description: 
published: true
date: 2022-03-22T22:05:27.596Z
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