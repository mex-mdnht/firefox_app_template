
# プロジェクトの上位フォルダ、ホームフォルダで
# npm install wrench rehab
# 上記実行し必要モジュールを入れておく

{exec} = require 'child_process'
Rehab = require 'rehab'

#パッケージするcoffeescriptソースのルートフォルダ
source_dir = 'coffee'

#書き出すファイルパス
build_file = 'package/js/app.js'

#最優先読み込みするファイル
before_list = [
]

#最後に読み込むファイル
after_list = [
	"coffee/App.coffee"
]

build = ->
	console.log "Building project from #{source_dir} to #{ build_file }"

	files = new Rehab().process source_dir
	mix_list = before_list.concat(after_list)
	filter_list = []
	for i in [0...files.length]
		unless files[i] in mix_list
			filter_list.push(files[i])

	to_single_file = "--join #{build_file}"
	from_files = "--compile #{before_list.join ' '} #{filter_list.join ' '} #{after_list.join ' '}"

	exec "coffee #{to_single_file} #{from_files}", (err, stdout, stderr) -> 
		throw err if err

#Mac,Linux用
task 'build', 'Build coffee2js using Rehab', sbuild = ->
	build()

#Win用
task 'build_win', 'Build coffee2js using Rehab', sbuild = ->
	for i in [0...before_list.length]
		before_list[i] = before_list[i].replace('/', '\\')
	for i in [0...after_list.length]
		after_list[i] = after_list[i].replace('/', '\\')
	build()

