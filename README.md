firefox_app_template
====================
set yourproject.sublime-oriject as below.



{
	"folders":
	[
	{
		"path": "/C/Users/maeda/Documents/works/private/firefox_app_template"
	}
	],
	"build_systems":
	[
		{"cmd":["cake.cmd","build_win"],
		"name": "CoffeeScriptJoin",
		"selector": "source.coffee"
		},
		{"cmd":[
			"$packages\\LESS-build\\dotless.Compiler.exe",
			"-m",
			"$project_path/less/app.less",
			"$project_path/package/css/app.css"
			],
			"file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
			"name": "LESS_in_AnotherFolder_minify",
			"selector": "source.css.less"
		}
	]
}

