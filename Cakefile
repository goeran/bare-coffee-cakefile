FILE_ENCODING = 'utf-8'

{exec} = require 'child_process'
fs = require 'fs'
util = require 'util'

task 'sbuild', (options) ->
	console.log "Compiling coffee scripts"
	exec "coffee --compile --output scripts/ src/", (err, stdout, stderr) ->
		if err
			stdout += stderr

		console.log stdout

	invoke 'run_specs'


task 'run_specs', () ->	
	console.log 'Running tests'
	phantom_dir = "Scripts/libs/phantom-jasmine"
	phantom_jasmine_runner = "#{phantom_dir}/run_jasmine_test.coffee"
	spec_runner = "specs/runnner.html"

	exec "phantomjs #{phantom_jasmine_runner} #{spec_runner}", (err, stdout, stderr) ->
		if err
			stdout += err

		console.log stdout