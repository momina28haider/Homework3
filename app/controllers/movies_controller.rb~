# This file is app/controllers/movies_controller.rb
class MoviesController < ApplicationController
	@sheettype = 'application'
  def index
	sort = params[:sort]
	ratings = params[:ratings]
	@all_ratings = Movie.all_ratings
	@selected_ratings = params[:ratings] || {}
	
	case sort
	when "title"
		@movies = Movie.find(:all, :order=>sort)
		ordering = {:order=>sort}
		@cstag = 'application'
		if @selected_ratings = {}
			return @movies
		end
	when "release_date"
		@movies = Movie.find(:all, :order=>sort)
		ordering = {:order=>sort}
		@cstag = 'application'
		if @selected_ratings = {}
			return @movies
		end
	end
	
	if @selected_ratings != {}
		@movies = Movie.find_all_by_rating(params[:ratings].keys, ordering)
		@cstag = 'application'
		return @movies
	end
		@movies = Movie.all
  end

  def show
    id = params[:id] # retrieve movie ID from URI route
    @movie = Movie.find(id) # Look up movie by unique ID
    # will render app/views/movies/show.<extension> by default
  end

  def new
    # default: render 'new' template
  end

  def create
    @movie = Movie.create!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully created."
    redirect_to movies_path
  end

  def edit
    @movie = Movie.find params[:id]
  end

  def update
    @movie = Movie.find params[:id]
    @movie.update_attributes!(params[:movie])
    flash[:notice] = "#{@movie.title} was successfully updated."
    redirect_to movie_path(@movie)
  end

  def destroy
    @movie = Movie.find(params[:id])
    @movie.destroy
    flash[:notice] = "Movie '#{@movie.title}' deleted."
    redirect_to movies_path
  end

end
