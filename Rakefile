task default: ['haml:convert_all']

namespace :haml do
  require 'haml'

  # Convert HAML files throughout the source-tree into their HTML counterparts
  folders = [:includes, :layouts]
  task convert_all: ([:root] + folders)

  def convert(file, destination)
    base_name = File.basename(file, '.haml') + '.html'
    html = File.open(file, 'r') { |f| Haml::Engine.new(f.read).render }
    File.open(File.join(destination, base_name), 'w') { |f| f.write html }
  end

  task :root do
    Dir.glob('./_haml/*.haml') { |path| convert path, './' }
  end

  folders.each do |folder|
    task folder do
      Dir.glob("./_#{folder}/_haml/*.haml") do |path|
        convert path, "./_#{folder}"
      end
    end
  end

end
