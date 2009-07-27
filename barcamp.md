!SLIDE
# El camino a la felicidad
# con Ruby on Rails
### Barcamp Valencia
<small>http://spainrb.org/felipe-talavera</small>

!SLIDE
# ¿ Felicidad ?

!SLIDE
# ¿ Pero que dices ?

!SLIDE
# Felicidad:
### Sensación de plenitud, alegría, goce y realización

!SLIDE
# Felicidad (aplicada al software)
### Poder entregar software de mayor calidad, en menos tiempo. y con menos esfuerzo.

!SLIDE
#Ruby on rails
>is an open-source framework that's optimized
>for programmer **happiness** and sustainable productivity. 

>It lets you write beautiful code by favoring convention over configuration.

!SLIDE
# Ruby => Lenguaje
# Rails => Framework

!SLIDE
# RUBY
>is a dynamic, open source programming language with a focus on simplicity and productivity.

>It has an elegant syntax that is natural to read and easy to write.

!SLIDE
# RUBY
Ruby originated in Japan during the mid-1990s and was initially 
developed and designed by Yukihiro "Matz" Matsumoto. 

It is based on Perl, Smalltalk, Eiffel, Ada, and Lisp.

!SLIDE
# RUBY
>Make the computer work for you.

>Design the language and libraries for people first

!SLIDE
@@@ ruby
	happiness = "I am happy :)"
	
	puts happiness
@@@

!SLIDE
@@@ ruby
	happiness = "I am happy :)"

	3.times { puts happiness }

	=> "I am happy :)"
	=> "I am happy :)"
	=> "I am happy :)"
@@@

!SLIDE
# RUBY
* Todo son objetos, ¡todo todo!
* Todo es extensible.
* Lenguaje natural, facil de leer
* Principio de mínima sorpresa
* Muy zen


!SLIDE
#Ruby on rails
>Rails was created in 2003 by David Heinemeier Hansson and has since been extended 
>by the Rails core team, more than 1,400 contributors, and supported by a vibrant ecosystem.

!SLIDE
>“Ruby on Rails is a breakthrough in lowering the barriers of entry to programming. Powerful web applications that formerly might have taken weeks or months to develop can be produced in a matter of days.”

-Tim O'Reilly, Founder of O'Reilly Media

!SLIDE
# DRY (Don't Repeat Yourself)
# KISS (Keep It Simple Stupid)
# MVC (modelo-vista-controlador)

!SLIDE

## MVC (modelo-vista-controlador)

![mvc](mvc.png)

Los tres componentes son:

* ActionRecord - Modelo
* ActionView - Vista
* ActionController - Controlador

!SLIDE
### Active Record

* Es la capa ORM (object-relacional mapping)
* Conecta con distintas bases da datos, como: db2, mysql, oracle, Postgres, SQLserver y SQLite.
* Falicita el establecimiento de relaciones (has_one, belong_to, has_many, belong_to_has_many)
* Comprueba de datos antes de pasarlos a la db - validations
* CRUD (create, read, update, delete) en la base de datos de manera muy sencilla y cómoda.
* No necesitamos tocar SQL, ej: Car.find(:all)
* Usamos Migraciones para definir el schema de la base de datos.

!SLIDE

@@@ ruby
class Car < ActiveRecord::Base
  belongs_to :owner
  has_many :wheels
  has_one :engine

  validates_presence_of  :driver

	def	serial_number
		"KEOD EDPE SKDL"
	end
end
@@@

!SLIDE
### Active Controller
* Encargada de recibir la petición, procesarla y devolver el resultado, es la unión entre activeRecord y activeView
* Encargadas de procesar los datos que vienen del navegador y hacer una petición al ActiveRecord, al actionMailer o renderizar algo con ActiveWiev, osea enrutar la petición.
* Mantiene la session y las cookies
* Soporte REST (Representational state transfer)

!SLIDE
@@@ ruby
class CarsController < ApplicationController
  # GET /cars
  # GET /cars.xml
  def index
    @cars = Car.all
    respond_to do |fo rmat|
      format.html # index.html.erb
      format.xml  { render :xml => @shops }
    end
  end

  # GET /cars/1
  # GET /cars/1.xml
  def show

    @car = Car.find(params[:id])

    respond_to do |format|
      format.html # show.html.erb
      format.xml  { render :xml => @shop }
    end
  end
end

@@@


!SLIDE
### ActiveView
* Sistema de vistas mediante plantillas, llamadas desde las acciones del controlador o desde otras plantillas.
* Las plantillas normalmente son html, xml, en el que se ha incustrado código ruby, erb, rxml, RJS, haml.
* Siempre que queramos reusar codigo podemos usar Helper.

!SLIDE
### ActiveView
&lt;h1&gt;Listing Cars&lt;/h1&gt;

&lt;table&gt;

  &lt;tr&gt;

  &lt;/tr&gt;

&lt;% @cars.each do |car| %&gt;

&lt;tr&gt;

&lt;td&gt;&lt;%= link_to &#x27;Show&#x27;, cars %&gt;&lt;/td&gt;

&lt;td&gt;&lt;%= link_to &#x27;Edit&#x27;, edit_cars_path(car) %&gt;&lt;/td&gt;

&lt;td&gt;&lt;%= link_to &#x27;Destroy&#x27;, cars, :confirm =&gt; &#x27;Are you sure?&#x27;, :method =&gt; :delete %&gt;&lt;/td&gt;

&lt;/tr&gt;

&lt;% end %&gt;

&lt;/table&gt;

&lt;br /&gt;

&lt;%= link_to &#x27;New Car&#x27;, new_car_path %&gt;

!SLIDE
### Otras cositas
* Scripts de generación de código.
* Sistema de test de "fábrica" con Unit::Test o con otras herramientas RSpec, Shoulda, cucumber
* Consola irb, nos permite probar nuestro codigo de manera interactiva.
* Debugger nos permite comprobar el codigo en tiempo de ejecución
* ActiveResource, nos permite consumir apis de manera nativa.
* Potente sistema de plugins, para hacer casi de todo. http://github.com es tu amigo :)
* Distintos stacks para hacer deploy: nginx + mongrel, nginx/apache + passenger, etc...
* Herramientas de automatización rake, capistrano

!SLIDE
# Buenas Prácticas

* SCM => git
* La comunidad se precupa mucho por el testing, TDD, BDD, Integración Continua, 
* Pair Programming
* metodologias agiles.

!SLIDE
# The future
Ahora Rails 2.3.3 vamos hacia... 
## rails + merb = Rails3

!SLIDE
#DEMO
¿Tenemos tiempo?


!SLIDE

# + INFO
* http://rubyonrails.org
* http://guides.rubyonrails.org
* http://wiki.rubyonrails.org

## listas de correo
* http://lists.simplelogica.net/mailman/listinfo/ror-es

## Estos apuntes
https://github.com/flype/barcamp_valencia/tree

!SLIDE
# GRACIAS

<!--
	 Estructura a seguir:

	Felicidad: definición, porque? rails
	Rails: definición
	Ruby: Presentación, ejemplos, filosofia
	Rails: Intro, historia, filosofia, arquitectura básica, Ecosistema, Ventajas
				 Buenas practicas  
				plugins, testing, debug,  Rest
-->