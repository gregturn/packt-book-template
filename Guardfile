require 'asciidoctor'
require 'erb'

options = {:attributes => ['allow-uri-read'] }

guard 'shell' do
  watch(/^.*\.adoc$/) {|m|
  	puts "Looking at " << m[0]
  		puts "Time to rebuild " << m[0]
  		Asciidoctor.convert_file(m[0], :safe => Asciidoctor::SafeMode::UNSAFE, :attributes => {'allow-uri-read' => '', 'copycss' => ''})
  }
end

# TODO:  If you want to convert 1/fragment_01.txt (etc.) into 1/processed_fragment_01.txt, plugin your custom script.
guard 'shell' do
  watch(/^(.*)\/(fragment_.*\.txt)$/) {|m|
    puts "Time to rebuild #{m[1]}/#{m[2]}"
    # system("my_script_to_convert < #{m[1]}/#{m[2]} > #{m[1]}/processed_#{m[2]}")
  }
end

# Run a LiveReload server. Find your browser's LiveReload plugin here => http://livereload.com/extensions/
guard 'livereload' do
  watch(%r{^.+\.(css|js|html)$})
end