require 'rubygems'

HEADER = /((^\s*\/\/.*\n)+)/

desc "rebuild the spectrum.js files for distribution"
task :build do
  begin
    require 'closure-compiler'
  rescue LoadError
    puts "closure-compiler not found.\nInstall it by running 'gem install closure-compiler"
    exit
  end
  source = File.read 'spectrum.js'
  header = source.match(HEADER)
  File.open('spectrum-min.js', 'w+') do |file|
    file.write header[1].squeeze(' ') + Closure::Compiler.new.compress(source)
  end
end
