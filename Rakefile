task default: ['haml:root']

namespace :haml do
  require 'haml'

  def convert(file, destination)
    base_name = File.basename(file, '.haml') + '.html'
    html = File.open(file, 'r') { |f| Haml::Engine.new(f.read).render }
    File.open(File.join(destination, base_name), 'w') { |f| f.write html }
  end

  task :root do
    Dir.glob('./_haml/*.haml') { |path| convert path, './' }
  end

end
